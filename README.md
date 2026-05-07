# Sushi Restaurant Management System

A full-stack web application for managing a sushi restaurant with two service modes — **all you can eat** and **à la carte**. Clients scan a QR code at their table, browse the menu, and place orders directly from their phone. Staff manage orders in real time, and admins control everything from the menu to pricing and statistics.

---

## 🌐 Live

| Service | Platform | URL |
|---|---|---|
| Frontend | Vercel | https://sushi-app-lac.vercel.app |

---

## 🔑 Test Credentials

You can log in and explore the app with the following accounts:

| Role | Username | Password | Access |
|---|---|---|---|
| **Admin** | admin | 123 | Full access — menu, tables, users, stats, settings |
| **Staff** | staff | 123 | Order management — view and update incoming orders |
| **Dashboard** | dashboard | 123 | Dashboard view |

> 💡 To test the **client experience**, scan or open the link below with a phone:
> [https://sushi-app-lac.vercel.app/client?table=1](https://sushi-app-lac.vercel.app/client?table=1)
>
> **Note:** The table must be open for the client interface to work. To open a table, log in as **dashboard** and open it from the dashboard.

---

## 📱 Client Access via QR Code

Clients access the app by scanning a **QR code placed on their table**. Each code points to a unique URL that automatically identifies the table and loads the menu:

```
https://sushi-app-lac.vercel.app/client?table=1
https://sushi-app-lac.vercel.app/client?table=2
https://sushi-app-lac.vercel.app/client?table=3
...
```

No app to install. No account needed. Customers scan, browse, and order — all from their own phone.

---

## 📌 Overview

This system was built to fully manage a sushi restaurant that supports two service modes — **all you can eat** and **à la carte** — selectable per table. In rodízio mode, customers pay a fixed price per person and order freely from the menu, with certain items marked as **EXTRA** at an additional cost. In à la carte mode, every item has its own price and customers pay for exactly what they order.

The app supports three distinct roles — **Admin**, **Staff**, and **Client** — each with their own dedicated interface.

**Admins** manage the entire restaurant from a single panel: the menu, categories, item availability, extras pricing, the rodízio fixed price, tables, staff accounts, and restaurant settings. They also have access to a statistics dashboard with revenue and order data.

**Staff** see all incoming orders grouped by table in real time, with a sound notification when a new order arrives. They update order status — from *Em preparação* to *Entregue* — directly from their screen.

**Clients** scan the QR code on their table and land on a clean mobile menu, already linked to their table. The service type (rodízio) is shown on their interface. Most items are included in the fixed price — items marked as **EXTRA** carry an additional cost. Clients add items to a cart and confirm the order, which immediately appears on the staff screen.

The app is fully **responsive**, working on any device — essential for clients on phones and staff on tablets.

---

## 🖥️ Screens & Functionality

### 🍱 Admin — Menu Management

The main admin panel shows the full menu organised by category (Bebidas, Entradas, Gunkan, Maki, Niguiri, Sashimi, Sobremesas, Temaki, Uramaki). Each item displays its photo, name, description, price, category badge, and whether it's marked as **EXTRA**.

From this screen, admins can:
- Filter items by category using the top tab bar
- **Edit** any item (pencil icon) — name, description, price, image, category, extra status
- **Delete** any item (trash icon)
- **Toggle visibility** of an item (eye icon) — hide it from the client menu without deleting it
- **Add new items** via the floating `+` button
- **Add new categories** via the `+ Categoria` button in the tab bar
- Access all other sections from the top navbar: Estatísticas, Mesas, Rodízio settings, Utilizadores, Novo user, Definições

Items with a **MÁX** badge show the maximum quantity a client can order of that item per table.

---

### 📋 Staff — Order Management

The staff screen shows all active orders grouped by table, in real time. A counter in the header shows the number of pending orders. Staff can also toggle a **sound alert** on/off to be notified when new orders arrive.

Each order card shows:
- The **table number** and number of pending orders for that table
- The **time** the order was placed
- The **current status** — *Em preparação* or *Entregue*
- The list of **items ordered** with quantities

Staff can update the order status directly from the card:
- **Em preparação** — marks the order as being prepared (orange, active state)
- **Entregue** — marks the order as delivered to the table

---

### 📱 Client — Menu (Mobile via QR Code)

The client interface is designed for mobile and accessed by scanning the QR code on the table. The table number and service type (**Rodízio**) are shown at the top.

The menu is organised by category, filterable via a horizontal scroll tab bar at the top. Each item shows:
- A photo
- Name and short description
- Price — **€0.00** for included items, or the extra price for **EXTRA** items
- An **Adicionar** button to add it to the cart
- An **ℹ️** icon to see full item details

At the bottom of the screen, a collapsible **cart panel** shows:
- The number of items and total price (extras only)
- Each item with its price, quantity controls (`−` / `+`), and a remove button
- A **Confirmar pedido** button to send the order to the kitchen

Once confirmed, the order appears instantly on the staff screen.

---

### 🪑 Table Management

The table management screen shows all restaurant tables in a grid. Each card displays the table number and its current status.

- **Green highlight + pax count** — table is occupied, showing how many people are seated
- **Livre** (grey) — table is free and available

The header shows a summary: *X de Y abertas* (how many tables are currently open out of the total). Admins can open, close, and manage tables from this view.

---

## ✨ Features Summary

### 🔐 Authentication & Authorization
- JWT-based login with access and refresh tokens
- Role-based access control — Admin, Staff, Client
- Protected routes on frontend and backend
- Unauthorized access redirects to a NoAccess page

### 🍱 Menu Management (Admin)
- Create, edit, and delete categories and items
- Set name, description, price, image, and category per item
- Mark items as **EXTRA** (charged on top of the rodízio price)
- Set a **maximum quantity** per item per order
- Toggle item visibility without deleting it

### 🎡 Service Mode Configuration (Admin)
- Two service modes supported: **All you can eat** and **À la carte**
- In rodízio mode, a fixed price per person is charged — configurable by the admin
- Items can be marked as **EXTRA** in _all you can eat_ mode, carrying an additional charge on top of the fixed price
- In à la carte mode, each item has its own price and customers pay per item
- All prices, limits, and service mode settings are fully adjustable from the admin panel

### 🪑 Table Management
- View all tables and their real-time status
- See how many people are at each occupied table
- Open and close tables

### 📦 Order Management
- Clients place orders from their phone via QR code
- Orders appear instantly on the staff screen, grouped by table
- Staff update order status: *Em preparação* → *Entregue*
- Sound notification alerts staff to new orders

### 👥 User Management (Admin)
- Create and manage admin and staff accounts
- Control access and roles across the system

### 📊 Statistics (Admin)
- Revenue summaries
- Order volume over time
- Most popular items

### ⚙️ Settings (Admin)
- Restaurant configuration via a dedicated Definições panel

---

## 🛠️ Tech Stack

### Backend
| Technology | Purpose |
|---|---|
| Node.js | Server runtime |
| Express.js | REST API framework |
| MongoDB Atlas | Cloud database |
| Mongoose | MongoDB object modeling |
| JWT (jsonwebtoken) | Access & refresh token authentication |
| bcrypt | Password hashing |

### Frontend
| Technology | Purpose |
|---|---|
| React | UI library |
| Vite | Build tool and dev server |
| React Router | Client-side routing and protected routes |
| Tailwind CSS | Utility-first styling |

### Deployment
| Layer | Platform |
|---|---|
| Frontend | Vercel |
| Backend | Render |
| Database | MongoDB Atlas |

---

## 📄 License

This project is private. All rights reserved.
