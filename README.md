# UniGO - University Carpooling App

A Flutter-based carpooling application designed for university students to share rides to campus. The app connects drivers with passengers heading to the same university, making commuting more affordable and sustainable.

## Features

### Core Functionality
- **Ride Publishing** - Drivers can publish rides with pickup/dropoff locations, schedule, passenger capacity, and pricing
- **Ride Search** - Passengers can search for available rides by destination, date, and passenger count
- **Ride Requests** - Passengers can request rides, and drivers can accept/reject requests
- **Real-time Chat** - In-app messaging between drivers and passengers with typing indicators and read receipts
- **Push Notifications** - FCM-based notifications for ride requests, acceptances, and new messages
- **User Profiles** - Profile management with completion tracking

### Key Features
- **Multi-step Onboarding** - Guided signup flow with 5 steps for complete user registration
- **Smart Location Selection** - Integrated location services with geocoding and reverse geocoding
- **Route Planning** - Distance calculation and route estimation using OpenStreetMap
- **Real-time Updates** - Firestore-powered real-time data synchronization
- **Message Caching** - Instant message display with local caching and background sync
- **Animated UI** - Smooth transitions, shimmer loading states, and message bubble animations

## Tech Stack

### Frontend
- **Flutter** - Cross-platform mobile framework
- **Dart** - Programming language (SDK ^3.8.1)

### Backend & Services
- **Firebase** - Backend infrastructure
  - **Cloud Firestore** - NoSQL database for real-time data
  - **Firebase Auth** - Authentication (email/password, Google Sign-In)
  - **Firebase Cloud Messaging** - Push notifications
  - **Firebase Core** - Firebase initialization

### Maps & Location
- **flutter_map** - OpenStreetMap widget for map display
- **latlong2** - Coordinate handling
- **geolocator** - Location services and GPS positioning

### UI & Utilities
- **google_fonts** - Custom typography
- **font_awesome_flutter** - Icon library
- **animations** - Smooth page transitions
- **shimmer** - Loading skeleton animations
- **awesome_snackbar_content** - Custom notification toasts
- **shared_preferences** - Local data persistence

## Project Structure

```
lib/
├── core/
│   ├── constants/
│   │   └── app_colors.dart          # App color scheme
│   ├── theme/
│   │   └── app_theme.dart           # Material theme configuration
│   ├── utils/
│   │   └── distance_utils.dart      # Distance calculations
│   └── widgets/
│       ├── base_map_widget.dart     # Reusable map component
│       ├── custom_button.dart       # Styled button
│       ├── custom_text_field.dart   # Styled input field
│       ├── passenger_ui_components.dart  # Passenger-specific widgets
│       ├── profile_skeleton.dart    # Profile loading skeleton
│       └── social_login_button.dart  # Social auth buttons
│
├── data/
│   ├── models/
│   │   ├── conversation_model.dart  # Chat conversation data
│   │   ├── message_model.dart       # Chat message data
│   │   ├── ride_model.dart          # Ride listing data
│   │   ├── ride_request_model.dart  # Ride request data
│   │   ├── search_ride_data.dart    # Search filters
│   │   ├── signup_data.dart         # Signup flow data
│   │   └── user_model.dart          # User profile data
│   └── services/
│       ├── auth_service.dart        # Authentication logic
│       ├── cached_location_service.dart  # Location caching
│       ├── cached_ride_data_service.dart  # Ride data caching
│       ├── conversation_service.dart  # Chat conversations
│       ├── location_service.dart    # Geocoding & location
│       ├── map_api_service.dart     # Map API integration
│       ├── message_cache_service.dart  # Message caching
│       ├── message_service.dart     # Messaging logic
│       ├── notification_service.dart  # Push notifications
│       ├── ride_request_service.dart  # Ride request management
│       ├── ride_service.dart        # Ride CRUD operations
│       └── user_service.dart        # User profile management
│
├── features/
│   ├── auth/
│   │   ├── screens/
│   │   │   ├── auth_wrapper.dart    # Auth state handler
│   │   │   ├── login_screen.dart    # Login UI
│   │   │   └── signup/
│   │   │       ├── signup_step1_screen.dart  # Basic info
│   │   │       ├── signup_step2_screen.dart  # University selection
│   │   │       ├── signup_step3_screen.dart  # Phone verification
│   │   │       ├── signup_step4_screen.dart  # Photo upload
│   │   │       └── signup_step5_screen.dart  # Profile completion
│   │
│   ├── inbox/
│   │   ├── screens/
│   │   │   ├── inbox_screen.dart    # Conversation list
│   │   │   └── chat_screen.dart     # Chat interface
│   │   └── widgets/
│   │       ├── chat_input_bar.dart  # Message input
│   │       ├── chat_shimmer.dart    # Chat loading skeleton
│   │       ├── inbox_tile.dart      # Conversation list item
│   │       ├── message_bubble.dart  # Message display
│   │       ├── ride_context_banner.dart  # Ride info in chat
│   │       └── typing_indicator.dart  # Typing animation
│   │
│   ├── map/
│   │   └── screens/
│   │       └── map_screen.dart      # Map display with pickup/dropoff
│   │
│   ├── navigation/
│   │   ├── entry_point.dart         # Main navigation container
│   │   ├── main_navigation.dart     # Navigation wrapper
│   │   └── navbar_widget.dart       # Bottom navigation bar
│   │
│   ├── onboarding/
│   │   └── screens/
│   │       └── welcome_screen.dart  # Welcome/onboarding
│   │
│   ├── profile/
│   │   └── screens/
│   │       └── profile_screen.dart  # User profile
│   │
│   ├── publish/
│   │   ├── models/
│   │   │   └── publish_ride_data.dart  # Publish flow state
│   │   ├── screens/
│   │   │   ├── dropoff_location_screen.dart  # University selection
│   │   │   ├── passenger_count_screen.dart  # Seat capacity
│   │   │   ├── pickup_location_screen.dart  # Pickup location
│   │   │   ├── pin_pickup_location_screen.dart  # Pin pickup on map
│   │   │   ├── price_estimate_screen.dart  # Set pricing
│   │   │   ├── publish_screen.dart  # Publish main screen
│   │   │   ├── ride_schedule_screen.dart  # Date/time selection
│   │   │   └── route_selection_screen.dart  # Route confirmation
│   │   └── publish_ride.dart        # Publish flow coordinator
│   │
│   ├── rides/
│   │   └── screens/
│   │       └── your_rides_screen.dart  # My rides (driver/passenger)
│   │
│   └── search/
│       ├── screens/
│       │   ├── destination_location_screen.dart  # Destination selection
│       │   ├── search_date_screen.dart  # Date selection
│       │   ├── search_passenger_screen.dart  # Passenger count
│       │   ├── search_results_screen.dart  # Search results
│       │   ├── search_screen.dart    # Search main screen
│       │   └── source_location_screen.dart  # Pickup location
│
├── widgets/
│   └── skeleton_loader.dart         # Generic skeleton loader
│
└── main.dart                        # App entry point
```

## Data Models

### Ride Model
- **Publisher Info** - Driver details with profile photo
- **Locations** - Pickup coordinates and university dropoff
- **Schedule** - Departure date and time
- **Route** - Distance, duration, and geometry
- **Capacity** - Total seats, available seats, pricing
- **Status** - Active, full, completed, cancelled
- **Passengers** - List of booked passenger IDs

### Ride Request Model
- **Requester** - Passenger details and contact
- **Driver** - Driver reference
- **Seats** - Number of seats requested
- **Pickup** - Custom pickup location
- **Status** - Pending, accepted, rejected, cancelled
- **Timestamps** - Created at, responded at

### Message Model
- **Content** - Text, image, or location
- **Sender** - Sender details with photo
- **Read Receipts** - List of users who read the message
- **Status** - Sent, delivered, read, failed
- **Timestamp** - Message creation time

## Getting Started

### Prerequisites
- Flutter SDK (3.8.1 or higher)
- Dart SDK
- Firebase project with:
  - Authentication enabled (Email/Password, Google)
  - Firestore database
  - Cloud Messaging

### Setup

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd carpool
   ```

2. **Install dependencies**
   ```bash
   flutter pub get
   ```

3. **Configure Firebase**
   - Create a Firebase project at [firebase.google.com](https://firebase.google.com)
   - Add an Android app (package name: `com.example.unigo`)
   - Add an iOS app (bundle ID: `com.example.unigo`)
   - Download `google-services.json` (Android) and `GoogleService-Info.plist` (iOS)
   - Place config files in appropriate directories:
     - Android: `android/app/google-services.json`
     - iOS: `ios/Runner/GoogleService-Info.plist`

4. **Enable Firebase services**
   - Authentication: Enable Email/Password and Google Sign-In
   - Firestore: Create database with production mode
   - Cloud Messaging: Enable for push notifications

5. **Set up Firestore Security Rules**
   - Configure rules to authenticate users and validate data access
   - Reference the production rules for proper setup

6. **Run the app**
   ```bash
   flutter run
   ```

### Environment Variables

Create a `.env` file in the project root:

```env
# Map API Configuration (if using custom map provider)
MAP_API_KEY=your_api_key_here
```

## Key Services

### Ride Service
Manages ride CRUD operations, search functionality, and booking management.

### Ride Request Service
Handles ride request creation, acceptance, rejection, and cancellation with atomic Firestore transactions.

### Message Service
Provides real-time messaging with caching, typing indicators, and read receipts.

### Notification Service
FCM-based push notifications with smart navigation to chat or rides screens.

### Location Service
Geocoding, reverse geocoding, and distance calculations using OpenStreetMap.

### Conversation Service
Manages chat conversations between drivers and passengers with ride context.

## Navigation

The app uses a bottom navigation bar with 5 tabs:

1. **Search** - Find available rides
2. **Publish** - Create a new ride listing
3. **Your Rides** - View published rides and requests (driver/passenger)
4. **Inbox** - Chat conversations
5. **Profile** - User profile and settings

## Authentication Flow

1. **Welcome Screen** - App introduction
2. **Login/Signup** - Authentication selection
3. **Multi-step Signup** - Progressive profile completion:
   - Step 1: Basic information (name, email)
   - Step 2: University selection
   - Step 3: Phone verification
   - Step 4: Profile photo
   - Step 5: Additional preferences
4. **Main App** - Full access to features

## Push Notifications

The app supports several notification types:

- `new_message` - New chat message (navigates to chat)
- `ride_request_received` - New ride request (navigates to Your Rides)
- `ride_request_accepted` - Request accepted (navigates to chat or Your Rides)

## Performance Optimizations

- **Message Caching** - Local cache for instant message display
- **Location Caching** - Cached location data for fast access
- **Ride Data Caching** - Cached ride information for offline viewing
- **Lazy Loading** - Pagination for messages and search results
- **Shimmer Loading** - Skeleton screens for smooth perceived performance

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Open a pull request

## License

This project is licensed under the MIT License.

## Support

For issues and questions, please open an issue on the GitHub repository.

---

Built with Flutter and Firebase
