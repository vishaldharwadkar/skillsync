# 🏗 SkillSync — System Architecture

## **1. Overview**
SkillSync is a **Skill Recommendation & Tracking Platform** designed to:
- Help users identify, learn, and track in-demand skills.
- Use **Machine Learning** for personalized recommendations.
- Integrate **React (Frontend)**, **.NET Core (Backend)**, and **Python ML (FastAPI)** in a full-stack setup.

---

## **2. High-Level Architecture**
[ React + TypeScript (Frontend)]
[ .NET Core Web API (Backend) ] <----> [ SQL Server Database ]
[ Python + FastAPI (ML Service) ] <----> [ ML Model Files (.pkl) ]

---

## **3. Component Breakdown**

### **3.1 Frontend**
- **Tech Stack**: React, TypeScript, Vite, TailwindCSS
- **Testing**: Jest / Vitest
- **Key Responsibilities**:
  - User registration & login
  - Manage skills (add, edit, delete)
  - Display recommended skills
  - API communication with backend

---

### **3.2 Backend (.NET Core API)**
- **Tech Stack**: ASP.NET Core Web API, Entity Framework Core
- **Database**: SQL Server
- **Testing**: xUnit
- **Key Responsibilities**:
  - Expose secure REST APIs
  - Handle authentication (JWT)
  - CRUD operations for users & skills
  - Communicate with Python ML service

---

### **3.3 Machine Learning Service**
- **Tech Stack**: Python, FastAPI
- **Libraries**: pandas, scikit-learn, joblib
- **Key Responsibilities**:
  - Train ML models on skills dataset
  - Predict skill recommendations
  - Expose ML endpoints for backend

---

### **3.4 Database (SQL Server)**
- **Stores**:
  - User profiles
  - Skill data
  - User-skill relationships
  - Recommendation history
- **Entity Relationship Example**:
  - `User` —< `UserSkills` >— `Skill`

---

## **4. Data Flow**
1. **User Action**: User interacts with React UI.
2. **API Call**: Frontend sends request to .NET Core backend.
3. **Database Query**: Backend fetches/stores data in SQL Server.
4. **ML Request**: Backend calls Python FastAPI ML service.
5. **Prediction**: ML service processes data and returns recommendations.
6. **Response**: Backend sends results to frontend for display.

---

## **5. Deployment Plan**
- **Frontend**: Netlify / Vercel
- **Backend**: AWS Elastic Beanstalk / Azure App Service
- **ML Service**: Render / AWS EC2
- **Database**: AWS RDS / Azure SQL Database

---

## **6. Security Considerations**
- HTTPS for all API calls
- JWT-based authentication
- Role-based access control
- Input validation & sanitization
- Environment variables for sensitive data

---

## **7. Scalability**
- Stateless backend for horizontal scaling
- Dedicated ML service for independent scaling
- CDN for frontend static assets
- Database indexing & caching for performance
