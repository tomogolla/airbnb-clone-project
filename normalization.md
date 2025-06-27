# Normalization

## **Database schema overview (AirBNB Clone**

### Entities and relationships
This schema implememts a normalized relational database for an AirBnB-style booking platform with six core entities:
1. User
   - stores all user accounts with authentication details
   - roles: guest, host, admin
   - critical fields: email(unique), password_hash, role
  
2. Property
    - Contains listing information for rental properties
    - Relates to User through host_id (many-to-one)
    - Includes pricing, location, and descriptive data

3. Booking
  - Manages reservation transactions
  - Connects Users to Properties (many-to-many relationship)
  - Tracks booking dates, status, and total price

4. Payment
   - Records financial transactions for bookings
   - Relates one-to-one with Booking records
   - Stores payment method and amount

5. Review
  - Contains guest feedback for properties
  - Requires valid user and property relationships
  - Enforces rating constraints (1-5 stars)

6. Message
   - Handles communication between users
   - Tracks sender/recipient relationships

## **Normalization Approach**
This schema demonstrates third normal form (3NF) through:
1. Atomic Values - All fields contain single, indivisible values
2. No Partial Dependencies - All non-key attributes depend on the full primary key
3. No Transitive Dependencies - Non-key attributes depend only on the primary key

## **Key Design Features**
- UUID Primary Keys for all tables ensuring global uniqueness
- Referential Integrity through foreign key constraints
- Data Validation via:
  - ENUM types for restricted values
  - CHECK constraints (e.g., rating range)
  - NOT NULL requirements for essential fields

- Performance Optimization with:
  - Automatic primary key indexing
  - Strategic additional indexes on frequently queried fields

- Temporal Tracking using created_at/updated_at timestamps

## **Business Logic Enforcement**
The schema inherently supports application requirements through:
- Role-based access control (user.role)
- Booking state management (booking.status)
- Payment method tracking
- Review quality controls (rating constraints)

This normalized design provides a solid foundation for the AirBnB clone's data management needs while maintaining flexibility for future expansion.

