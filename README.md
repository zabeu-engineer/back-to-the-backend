# back-to-the-backend

# 🎮 Back-to-the-Backend: Retro Game Library

Welcome to the **Retro Game Library** challenge! Your mission is to build a robust REST API to manage a collection of classic video games using **Node.js**, **TypeScript**, and **Express**.

## 🎯 Technical Objectives
- Set up a professional Node.js environment with TypeScript.
- Implement the **MVC (Model-View-Controller)** pattern.
- Create secure routes with structured validation.
- Handle HTTP status codes appropriately (200, 201, 400, 404).

---

## 🏗️ Project Structure
To keep the code clean, follow this organization:
- `src/controllers`: Logic for handling requests and responses.
- `src/routes`: Definition of your API endpoints.
- `src/types`: TypeScript interfaces and custom types.
- `src/schemas`: Validation logic (using [Zod](https://zod.dev)) or [Joi](https://www.npmjs.com/package/joi).

---

## 🏗️ Data Model (Entity: `Game`)
Each game in your collection must follow this structure:

- **id**: A unique identifier (e.g., `crypto.randomUUID()`).
- **title**: Name of the game (e.g., "The Legend of Zelda").
- **platform**: Console name (e.g., "SNES", "Mega Drive").
- **year**: Release year (e.g., 1991).
- **genre**: Genre (e.g., "RPG", "Action").
- **status**: Current state (`"backlog"`, `"playing"`, `"completed"`).

---

## 🛠️ Required Endpoints

| Method | Endpoint | Description |
| :--- | :--- | :--- |
| **GET** | `/games` | Returns all games. Should allow filtering by platform via Query Params (e.g., `?platform=SNES`). |
| **GET** | `/games/:id` | Returns details for a single game. Return `404` if not found. |
| **POST** | `/games` | Registers a new game. Requires body validation. |
| **PATCH** | `/games/:id/status` | Updates only the `status` of a specific game. |

---

## 🛡️ Business Rules & Validation
For the **POST** endpoint, implement the following rules using a validation library:

1. **Title**: Required, string, minimum 3 characters.
2. **Year**: Must be between `1958` (Tennis for Two) and the **current year**.
3. **Platform**: Must be one of: `["NES", "SNES", "Mega Drive", "GameBoy", "PS1", "N64"]`.
4. **Status**: If not provided, default to `"backlog"`.
5. **Errors**: If validation fails, return `400 Bad Request` with a descriptive message.

---

## 🚀 Boss Level (Extra Challenges)

1. **Custom Middleware**: Create a logger that prints the `Method`, `URL`, and `Timestamp` for every incoming request.
2. **Data Persistence**: Instead of an array in memory, save and load your data from a `postgres` database.
3. **Advanced Filtering**: Allow the `/games` endpoint to filter by multiple criteria at once (e.g., platform AND status).
4. **Dockerization**: Create a docker file and a how-to run using containers.

---
**Happy coding, Player 1!** 🕹️
