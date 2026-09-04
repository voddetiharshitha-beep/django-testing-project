# Critical APIs for Mobile Application

## Objective

Identify and prioritize the APIs that are most important for a mobile ride-booking application.

## Selected Critical APIs

| Priority | API | Method | Suggested Endpoint | Why it is critical |
|---|---|---|---|---|
| P0 | Login | POST | `/api/login/` | Required to authenticate the mobile user before accessing protected features. |
| P0 | Nearby Drivers | GET | `/api/drivers/nearby/` | Helps a rider find available drivers around the pickup location. |
| P0 | Create Ride | POST | `/api/rides/` | Core business operation used to request/book a ride. |
| P0 | Driver Location | GET/WS | `/api/drivers/location/` | Provides current driver location and supports live tracking. |
| P0 | Ride Details | GET | `/api/rides/<id>/` | Allows the mobile app to display the current ride, driver, pickup, destination and fare information. |
| P1 | Notifications | GET/POST | `/api/notifications/` | Delivers important ride updates such as driver assignment, arrival and ride completion. |
| P1 | Ride History | GET | `/api/rides/history/` | Allows users to view previous rides, fares and statuses. |

## Criticality Classification

### P0 - Business Critical

These APIs should be treated as the highest priority because the mobile app cannot complete its main ride-booking flow without them:

1. Login
2. Nearby Drivers
3. Create Ride
4. Driver Location
5. Ride Details

### P1 - Important

These APIs are important for a complete mobile experience but are not required to start a new ride:

6. Notifications
7. Ride History

## Main Mobile Ride Flow

The expected mobile application flow is:

`Login`
→ `Nearby Drivers`
→ `Create Ride`
→ `Ride Details`
→ `Driver Location`

Supporting features:

`Notifications`
and
`Ride History`

## Testing Priority

Because these APIs are critical, automated API tests should prioritize them in this order:

1. Authentication and invalid-login scenarios
2. Create ride success and validation failures
3. Ride ownership/security
4. Nearby driver response and filtering
5. Ride details for valid and invalid ride IDs
6. Driver location updates
7. Notification delivery/read status
8. Ride history filtering and pagination

## Current Project Note

The uploaded Django project currently contains a `Product` API:

- `GET /api/products/`
- `POST /api/products/`
- `GET /api/products/<id>/`

The requested ride-related APIs are not currently implemented in this project. Therefore, this task documents the critical API selection and recommended priority without pretending that the ride APIs already exist.

## Acceptance Criteria

- [x] Critical mobile APIs identified.
- [x] APIs prioritized as P0/P1.
- [x] Purpose of each API documented.
- [x] Recommended endpoints documented.
- [x] Testing priority documented.
- [x] Current project limitations clearly identified.
