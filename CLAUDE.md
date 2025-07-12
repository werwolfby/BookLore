# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

BookLore is a full-stack web application for managing and reading digital books and comics. It consists of:
- **Frontend**: Angular 20 SPA in `booklore-ui/`
- **Backend**: Spring Boot 3.5 REST API in `booklore-api/`
- **Database**: MariaDB with Flyway migrations

## Essential Commands

### Frontend Development
```bash
cd booklore-ui
npm install          # Install dependencies
npm start            # Dev server on localhost:4200
npm run build        # Production build
npm test             # Run unit tests
npm run lint         # Run ESLint
```

### Backend Development
```bash
cd booklore-api
./gradlew bootRun    # Run development server
./gradlew build      # Build JAR
./gradlew test       # Run tests
```

## Architecture & Key Patterns

### Frontend Architecture
- **Components**: Uses Angular's standalone component architecture (no NgModules)
- **UI Library**: PrimeNG components are used throughout - always check PrimeNG docs for component APIs
- **State**: RxJS-based services in `src/app/shared/services/`
- **Models**: TypeScript interfaces in `src/app/shared/models/`
- **Real-time**: WebSocket support via RxStomp for notifications

### Backend Architecture
- **Layered Structure**: Controller → Service → Repository pattern
- **DTOs**: MapStruct for entity-DTO mapping
- **Security**: JWT authentication with Spring Security
- **API Docs**: Available at `/swagger-ui.html` when running

### Key Technologies
- **Frontend**: Angular 20, PrimeNG 19, Tailwind CSS, RxJS, epubjs
- **Backend**: Java 21, Spring Boot 3.5, Spring Data JPA, Flyway, MapStruct
- **Database**: MariaDB with JPA/Hibernate

## Important Development Notes

1. **TypeScript Strict Mode**: Frontend uses strict TypeScript - always handle null/undefined properly
2. **Standalone Components**: All Angular components use standalone API - no NgModules
3. **PrimeNG Integration**: Custom theme in `src/styles/` - maintain consistency
4. **WebSocket**: Real-time updates use STOMP over WebSocket
5. **File Storage**: Books stored in configurable paths - check `application.properties`
6. **Multi-format Support**: Handles PDF, EPUB, CBX/CBZ - each has specific reader implementation

## Testing Approach
- **Frontend**: Karma + Jasmine for unit tests
- **Backend**: JUnit with Spring Boot Test for integration/unit tests
- Run tests before committing changes

## Database Migrations
- Flyway migrations in `booklore-api/src/main/resources/db/migration/`
- Follow naming convention: `V{version}__{description}.sql`
- Test migrations locally before committing