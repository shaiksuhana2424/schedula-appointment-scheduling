# Schedula Appointment Scheduling System
## Entity-Relationship (ER) Diagram

```mermaid
erDiagram
    USER ||--o| PATIENT : has
    USER ||--o| DOCTOR : has
    DOCTOR ||--o{ AVAILABILITY : defines
    PATIENT ||--o{ APPOINTMENT : books
    DOCTOR ||--o{ APPOINTMENT : receives
    AVAILABILITY ||--o{ APPOINTMENT : schedules

    USER {
        int user_id PK
        string name
        string email
        string password_hash
        string role
    }

    PATIENT {
        int patient_id PK
        int user_id FK
        string phone
        date date_of_birth
    }

    DOCTOR {
        int doctor_id PK
        int user_id FK
        string specialization
        string phone
    }

    AVAILABILITY {
        int availability_id PK
        int doctor_id FK
        date available_date
        time start_time
        time end_time
    }

    APPOINTMENT {
        int appointment_id PK
        int patient_id FK
        int doctor_id FK
        int availability_id FK
        string status
        datetime created_at
    }
```

## Relationships

- A user account may be associated with a patient or doctor profile.
- A doctor can define multiple availability slots.
- A patient can book multiple appointments.
- A doctor can receive multiple appointments.
- Each appointment is associated with a patient, a doctor, and a scheduled slot.

## Notes

This is an initial schema and must be checked against the official Schedula API documentation before final approval.
