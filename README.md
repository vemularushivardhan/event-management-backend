# Event Management & Registration System - Backend API

Production-ready REST API built with **Spring Boot 3.3.4**, **Java 17/21**, **Spring Security (JWT)**, **Spring Data JPA**, **Hibernate**, and **MySQL 8.0**.

## Tech Stack
- **Framework**: Spring Boot 3.3.4
- **Language**: Java 17+ (Java 21 supported)
- **Security**: Spring Security 6 + JJWT 0.12.6 (Stateless JWT, Role-Based Access Control)
- **Persistence**: Spring Data JPA + Hibernate ORM
- **Database**: MySQL 8.0 (`event_management`)
- **QR Code Engine**: ZXing 3.5.3 (Generation & Verification)
- **Build Tool**: Maven 3.9+

## Prerequisites
1. **Java 17** or higher (`java -version`)
2. **Maven 3.8+** (`mvn -v`)
3. **MySQL 8.0** running locally on port 3306

## Database Setup
1. Log into your MySQL console:
   ```sql
   CREATE DATABASE IF NOT EXISTS event_management CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
   ```
2. The schema and sample data will be automatically created on startup via Hibernate and `DataInitializer.java`.
   - Alternatively, execute `database/schema.sql` and `database/sample-data.sql`.

## Configuration
Edit `src/main/resources/application.properties` if needed:
```properties
spring.datasource.url=jdbc:mysql://localhost:3306/event_management?createDatabaseIfNotExist=true&useSSL=false&allowPublicKeyRetrieval=true&serverTimezone=UTC
spring.datasource.username=root
spring.datasource.password=root2005
```

## How to Run
```powershell
mvn clean compile
mvn spring-boot:run
```
The server will start at `http://localhost:8080`.

## Default Demo Accounts
- **Admin**: `admin@eventmanagement.com` / `Admin@123`
- **User**: `alice.johnson@example.com` / `Password@123`

## REST API Overview
- `POST /api/auth/register` - User registration
- `POST /api/auth/login` - User/Admin authentication (returns JWT)
- `GET /api/auth/me` - Get current authenticated user profile
- `GET /api/events` - Browse public events (filtering by search & availability)
- `GET /api/events/{id}` - Get event details
- `POST /api/events` - Create event (Admin only)
- `PUT /api/events/{id}` - Update event (Admin only)
- `DELETE /api/events/{id}` - Delete event (Admin only)
- `POST /api/registrations/events/{eventId}` - Register for an event
- `GET /api/registrations/my` - View current user registrations
- `GET /api/registrations/{id}` - View registration pass & QR token
- `POST /api/registrations/{id}/cancel` - Cancel registration
- `POST /api/admin/attendance/check-in` - Scan/verify QR code and check in participant
- `GET /api/admin/dashboard/stats` - Admin dashboard metrics
- `GET /api/admin/reports` - Detailed event attendance reports
