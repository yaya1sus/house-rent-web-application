# HouseRent Review & Rating

## Feature rules
- Renter must be logged in.
- Renter can review only their own booking after `bookingStatus` becomes `booked`.
- One review per booking (unique `bookingId`).
- Rating: integer 1-5. Comment: 3-1000 characters.
- Property reviews and average rating can be read publicly.

## Add route in Backend/index.js
Alongside the existing API routes, add:
```js
app.use('/api/reviews', require('./routes/reviewRoutes'));
```

## API
- `GET /api/reviews/property/:propertyId` public: review list, `ratingAverage`, `ratingCount`.
- `POST /api/reviews` authenticated: `{ "bookingId": "...", "rating": 5, "comment": "..." }`.
- `GET /api/reviews/mine` authenticated: current renter's reviews.

The project currently writes `propertyId` from booking controller while BookingSchema declares the legacy typo `propertId`. The controller below accepts either propertyId field for compatibility.
