# ClassPlus - Personalized Greeting Cards Application

A full-stack web application for creating, customizing, and sharing personalized greeting cards with overlaid profile pictures and names.

## 🎯 Project Overview

ClassPlus enables users to:
- Select from various greeting card templates (Birthday, Anniversary, Festivals, etc.)
- Automatically overlay their profile picture and name onto templates
- Download and share personalized cards via WhatsApp, Instagram, Email, etc.
- Unlock premium templates through subscription

## 🏗️ Architecture

```
ClassPlus/
├── backend/                 # Node.js/Express API
│   ├── src/
│   │   ├── server.js       # Main Express application
│   │   ├── middleware/     # Auth & validation middleware
│   │   ├── models/         # MongoDB schemas (User, Template)
│   │   ├── routes/         # API endpoints
│   │   ├── controllers/    # Business logic
│   │   └── utils/          # Helper functions
│   ├── package.json
│   └── .env.example        # Environment variables
│
├── frontend/                # React SPA
│   ├── src/
│   │   ├── pages/          # Page components (Auth, Home, Editor)
│   │   ├── components/     # Reusable UI components
│   │   ├── context/        # React Context (Auth)
│   │   ├── services/       # API client
│   │   ├── styles/         # CSS stylesheets
│   │   ├── App.jsx         # Main app component
│   │   └── main.jsx        # Entry point
│   ├── package.json
│   └── public/
│
└── README.md
```

## 🛠️ Technology Stack

### Frontend
- **React 18** - UI library
- **React Router v6** - Client-side routing
- **Axios** - HTTP client
- **html2canvas** - Image generation from DOM
- **CSS3** - Styling

### Backend
- **Node.js** - Runtime
- **Express.js** - Web framework
- **MongoDB** - NoSQL database
- **Mongoose** - ODM
- **JWT** - Authentication
- **bcryptjs** - Password hashing
- **CORS** - Cross-origin support
- **Multer** - File uploads

## 📋 Features

### 2.1 Authentication
- ✅ Email/Password login and signup
- ✅ Google OAuth integration (ready)
- ✅ Guest login with name
- ✅ JWT-based token authentication

### 2.2 Home Page
- ✅ Categorized templates grid (Birthday, Anniversary, Festivals, etc.)
- ✅ Image listing with thumbnails
- ✅ Category filtering
- ✅ Live preview with user overlays

### 2.3 Personalization & Sharing
- ✅ Auto-overlay of profile picture and name
- ✅ Customizable text position, color, and size
- ✅ Download as PNG
- ✅ Generate shareable links (ready)
- ✅ Social sharing integration (WhatsApp, Email ready)

### 2.4 Premium Features
- ✅ Free vs Premium template distinction
- ✅ Premium badge display
- ✅ Subscription upgrade endpoints
- ✅ Subscription date tracking

## 🚀 Getting Started

### Prerequisites
- Node.js v16+
- MongoDB (local or Atlas)
- npm or yarn

### Backend Setup

1. Navigate to backend directory:
```bash
cd backend
```

2. Install dependencies:
```bash
npm install
```

3. Create `.env` file:
```bash
cp .env.example .env
```

4. Update `.env` with your configuration:
```
PORT=5000
MONGODB_URI=mongodb://localhost:27017/classplus
JWT_SECRET=your_secret_key_here
GOOGLE_CLIENT_ID=your_google_client_id
CORS_ORIGIN=http://localhost:3000
```

5. Start the backend:
```bash
npm run dev
```

Backend runs on `http://localhost:5000`

### Frontend Setup

1. Navigate to frontend directory:
```bash
cd frontend
```

2. Install dependencies:
```bash
npm install
```

3. Create `.env` file:
```
REACT_APP_API_URL=http://localhost:5000/api
```

4. Start the frontend:
```bash
npm run dev
```

Frontend runs on `http://localhost:3000`

## 📚 API Endpoints

### Authentication
- `POST /api/auth/signup` - Register new user
- `POST /api/auth/login` - Login with email
- `POST /api/auth/google` - Google OAuth callback
- `POST /api/auth/guest` - Guest login

### Templates
- `GET /api/templates` - Get all templates
- `GET /api/templates?category=Birthday` - Filter by category
- `GET /api/templates/:id` - Get template details
- `GET /api/templates/categories` - Get all categories

### Users
- `GET /api/users/profile` - Get user profile
- `PUT /api/users/profile` - Update profile
- `POST /api/users/upgrade-premium` - Upgrade subscription

### Sharing
- `POST /api/share/generate-link` - Create shareable link
- `GET /api/share/:shareId` - Get shared card data

## 🗄️ Database Schema

### User Model
```javascript
{
  email: String (unique),
  name: String,
  password: String (hashed),
  profilePicture: String (URL),
  googleId: String,
  authProvider: 'email' | 'google' | 'guest',
  isGuest: Boolean,
  subscription: 'free' | 'premium',
  subscriptionStartDate: Date,
  subscriptionEndDate: Date,
  createdAt: Date,
  updatedAt: Date
}
```

### Template Model
```javascript
{
  title: String,
  description: String,
  category: String,
  imageUrl: String,
  thumbnail: String,
  isPremium: Boolean,
  overlayConfig: {
    namePosition: { x, y },
    photoPosition: { x, y },
    photoSize: { width, height },
    nameColor: String,
    fontSize: Number
  },
  downloadCount: Number,
  createdAt: Date
}
```

## 🔐 Security Features

- ✅ JWT token-based authentication
- ✅ Password hashing with bcryptjs
- ✅ CORS protection
- ✅ Input validation with express-validator
- ✅ Environment variable management
- ✅ Token verification middleware

## 📱 Responsive Design

- Mobile-first approach
- Responsive grid layouts
- Touch-friendly buttons
- Optimized for all screen sizes

## 🚀 Deployment

### Backend (Node.js)
Deploy to:
- Heroku
- Railway
- Render
- AWS EC2

### Frontend (React)
Deploy to:
- Vercel
- Netlify
- GitHub Pages
- AWS S3 + CloudFront

## 📝 Usage Examples

### 1. Guest Login
```javascript
// No signup needed, just enter name
- Click "Guest" tab
- Enter your name
- Proceed to templates
```

### 2. Select Template
```javascript
- Browse templates by category
- Click "Select" button
- Template opens in editor
```

### 3. Customize & Share
```javascript
- View template with your picture & name
- Click "Download" to save as PNG
- Click "Share Card" to generate link
- Copy and paste in WhatsApp/Email/Instagram
```

## 🔄 Future Enhancements

- [ ] Advanced image editing tools
- [ ] Custom background upload
- [ ] Font selection
- [ ] Sticker/filter additions
- [ ] Scheduled sharing
- [ ] Template creation by users
- [ ] Analytics dashboard
- [ ] Payment gateway integration (Stripe/Razorpay)
- [ ] Mobile app (React Native)
- [ ] Video greeting cards

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit changes (`git commit -m 'Add AmazingFeature'`)
4. Push to branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 📧 Support

For support, email support@classplus.com or open an issue in the GitHub repository.

## 👥 Team

- **Frontend Lead**: [Your Name]
- **Backend Lead**: [Your Name]
- **UI/UX Designer**: [Your Name]

---

**Happy Card Making! 🎉**
