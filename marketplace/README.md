# Media Tech Support - Marketplace

A complete marketplace platform for buying and selling PCs, laptops, used devices, and android tools (rent & subscription).

## Features

### Marketplace
- **Categories**: PC, Laptop, Used Devices (Laptops, Mobiles, Computers), Android Tools (Rent, Subscription)
- **Search**: Full-text search across all products
- **Responsive Design**: Works on desktop, tablet, and mobile

### Authentication
- User registration with Seller/Buyer roles
- Login with username or email
- Password validation (letters, numbers, symbols, 8+ chars)
- Password reset flow

### Seller Features
- **Upload Products**: PC, Laptop, Used Devices with 6 images, name, company, description, price, location
- **Upload Tools (Subscription)**: 4 screenshots, name, description, duration, price
- **Upload Tools (Rent)**: 5 images, name, description, rent duration, price per day/hour
- **Payment Method Setup**: Bank Transfer, Easypaisa, JazzCash, NayaPay, SadaPay

### Buyer Features
- Browse and search products
- Product detail page with seller info (no contact details exposed)
- Add to cart or Buy Now
- **Device Purchase**: Enter shipping address, phone, city
- **Tool Subscription**: Enter email, phone, WhatsApp number
- **Tool Rental**: Enter email for access credentials
- **Payment**: Select wallet (NayaPay, Easypaisa, JazzCash) → see account details → submit proof
- **Payment Proof**: Enter amount, method, transaction ID, upload screenshot, email

### Admin Panel (Separate)
- Dashboard with stats (users, products, orders, payments)
- Manage Users (view, search, delete)
- Manage Products (view, search, delete)
- Manage Orders (view details, delete)
- View Payment Proofs with screenshots
- Export data as JSON
- Settings (admin credentials, API URL)

## File Structure

```
marketplace/
├── index.html              # Main marketplace page
├── login.html              # Login / Signup / Reset password
├── profile.html            # User profile + my products + my orders
├── seller-payment.html     # Seller payment method setup
├── upload.html             # Product/tool upload forms
├── product.html            # Product detail page
├── payment.html            # Buyer payment (wallet selection)
├── payment-proof.html      # Payment proof submission
├── css/
│   └── style.css           # Shared styles
├── js/
│   └── app.js              # Shared JavaScript (auth, products, orders, cart)
├── admin/
│   └── index.html          # Admin panel (separate code)
├── appscript/
│   └── Code.gs             # Google Apps Script backend
└── README.md               # This file
```

## Setup

### Frontend (Static Hosting)
1. Upload all files to any static hosting (GitHub Pages, Netlify, etc.)
2. Or open `index.html` directly in your browser for local testing

### Google Apps Script Backend
1. Go to [Google Apps Script](https://script.google.com)
2. Create a new project
3. Copy the code from `appscript/Code.gs`
4. Create a new Google Sheet and copy its ID from the URL
5. Replace `YOUR_GOOGLE_SHEET_ID` in Code.gs with your Sheet ID
6. Run `setupSheets()` once to create all required sheets
7. Deploy as Web App:
   - Click **Deploy** → **New Deployment**
   - Select **Web app**
   - Execute as: **Me**
   - Who has access: **Anyone**
   - Click **Deploy** and copy the Web App URL
8. Update `CONFIG.API_URL` in `js/app.js` with your Web App URL

### Admin Panel
- Navigate to `admin/index.html`
- Default credentials: `admin` / `admin123`
- Change credentials in Settings after first login

## Payment Accounts (Buyer Side)
The following accounts are configured for buyer payments:

| Wallet | Account Number | Account Name |
|--------|---------------|--------------|
| NayaPay | 03198595421 | Muhammad Ramzan ul sami |
| Easypaisa | 03198595421 | Muhammad Ramzan Al Sami |
| JazzCash | 03218595421 | Muhammad Ramzan Al Sami |

## Tech Stack
- **Frontend**: Pure HTML, CSS, JavaScript (no frameworks)
- **Backend**: Google Apps Script
- **Database**: Google Sheets
- **Storage**: LocalStorage (offline) + Google Sheets (online)

## Notes
- The marketplace works offline using localStorage as a fallback database
- When Google Apps Script is configured, data syncs to Google Sheets
- Demo products are automatically seeded on first visit
- All images are stored as base64 in localStorage (for demo); use Google Drive for production
