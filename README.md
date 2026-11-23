# CropCare – Crop Management System

CropCare is a modern, responsive full-stack crop management web application designed for agricultural monitoring, growth tracking, and harvest scheduling.

---

## 🌿 Features

- **Executive Dashboard**: Real-time summary metrics for:
  - **Total Crops** planted across all fields
  - **Growing** crops in active vegetative or reproductive cycles
  - **Ready for Harvest** crops requiring immediate harvesting scheduling
  - **Harvested** completed yields
- **Comprehensive Crop Registry (CRUD)**:
  - **Add Crop**: Register crops with Crop Name, Type (Grain, Vegetable, Fruit, Legume, Cash Crop, Herb, etc.), Field Location, Planting Date, Expected Harvest Date, Status, Acreage, and Notes.
  - **View Details**: Inspect individual crop growth timelines, calculated progress percentage, days remaining until harvest, and field observations.
  - **Edit Crop**: Modify status, timeline, notes, or field details with real-time UI updates.
  - **Delete Crop**: Safely remove crop records with an interactive confirmation modal.
- **Search & Filter Engine**:
  - Live search across crop names, field locations, crop types, and field notes.
  - Status quick-filter tabs (*All*, *Growing*, *Ready to Harvest*, *Harvested*).
  - Crop type dropdown filtering.
  - Multi-column sorting (Planting Date, Harvest Date, Name, Recency).
- **Persistent JSON Storage**:
  - All records are saved directly to `server/data/crops.json` on the server disk.
  - Pre-seeded with realistic sample crops across diverse field types and statuses.
- **Modern Green-and-White Design**:
  - Responsive desktop and mobile layout with sidebar navigation, summary cards, and clean data tables.

---

## 🛠️ Tech Stack

- **Frontend**: React 18, Vite, Lucide React Icons, Custom Modern CSS
- **Backend**: Node.js, Express, CORS
- **Storage**: Persistent JSON File Storage (`server/data/crops.json`)

---

## 📁 Project Structure

```text
CropCare/
├── client/                     # React + Vite Frontend
│   ├── src/
│   │   ├── components/         # UI components
│   │   │   ├── Sidebar.jsx
│   │   │   ├── Header.jsx
│   │   │   ├── SummaryCards.jsx
│   │   │   ├── CropTable.jsx
│   │   │   ├── CropFormModal.jsx
│   │   │   ├── CropDetailModal.jsx
│   │   │   ├── DeleteConfirmModal.jsx
│   │   │   └── Toast.jsx
│   │   ├── services/
│   │   │   └── api.js          # REST API client
│   │   ├── App.jsx             # Main application component
│   │   ├── index.css           # Green-and-white theme styles
│   │   └── main.jsx
│   ├── index.html
│   ├── package.json
│   └── vite.config.js
├── server/                     # Express REST API Backend
│   ├── data/
│   │   └── crops.json          # Persistent JSON storage
│   ├── package.json
│   ├── server.js               # Express API endpoints
│   └── test-in-memory.js       # Automated CRUD test suite
├── .gitignore
├── package.json                # Root package with concurrently
└── README.md
```

---

## 🚀 Getting Started

### 1. Prerequisites
- **Node.js** (v18 or newer)
- **npm** (v9 or newer)

### 2. Run the Application

From the root directory (`CropCare/`), run:

```bash
npm run dev
```

This concurrently starts:
1. **Backend Server**: `http://localhost:5000`
2. **Frontend App**: `http://localhost:3000`

Open [http://localhost:3000](http://localhost:3000) in your browser to start managing crops!

### Running Components Individually

- **Backend only**:
  ```bash
  npm run server
  ```
- **Frontend only**:
  ```bash
  npm run client
  ```

---

## 🧪 Running Tests

An automated CRUD verification test suite is included:

```bash
npm test
```

This verifies:
- Health check endpoint (`GET /api/health`)
- Summary statistics (`GET /api/crops/stats`)
- Fetching crop listings (`GET /api/crops`)
- Creating a new crop (`POST /api/crops`)
- Fetching by ID (`GET /api/crops/:id`)
- Updating a crop (`PUT /api/crops/:id`)
- Search & filtering (`GET /api/crops?search=...`)
- Deleting a crop (`DELETE /api/crops/:id`)
- 404 handling and JSON file persistence

---

## 📡 REST API Reference

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/api/health` | Service health status |
| `GET` | `/api/crops/stats` | Aggregated crop metrics (total, growing, ready, harvested, acres) |
| `GET` | `/api/crops` | List crops (query params: `search`, `status`, `type`, `sortBy`, `sortOrder`) |
| `GET` | `/api/crops/:id` | Get single crop details |
| `POST` | `/api/crops` | Create new crop record |
| `PUT` | `/api/crops/:id` | Update existing crop record |
| `DELETE` | `/api/crops/:id` | Delete crop record |

---

## 📝 License

MIT
