# 🏔️ TrailBag — Backpacking Recipe Planner

> **Made with Claude** · A single-file web app for planning and optimizing backpacking meals.

TrailBag helps you build dehydrated/freeze-dried meal recipes, track nutritional data, calculate water requirements, and rank recipes by caloric density — everything you need to pack smart and eat well on trail.

---

## Features

- **Recipe Builder** — Create multi-ingredient meal recipes with per-gram nutritional data
- **Serving Scaler** — Scale any recipe up or down and watch all weights, water, and macros update live
- **Water Calculator** — Automatically computes rehydration water needed per ingredient based on rehydration ratios
- **Caloric Density Rankings** — Ranks all your recipes by calories per ounce of dry weight so you know what earns its pack space
- **Nutrition Breakdown** — Tracks calories, fat, sodium, carbs, fiber, and protein per recipe
- **Printable Recipe Cards** — Generates a clean, print-ready card for each recipe with an ingredient table and nutrition summary
- **Import / Export** — Back up and restore your entire ingredient and recipe database as JSON
- **Persistent Storage** — All data saved to `localStorage`; your recipes survive page refreshes

---

## Usage

No build step, no dependencies to install. Just open the file.

```bash
# Clone the repo
git clone https://github.com/your-username/trailbag.git
cd trailbag

# Open directly in your browser
open trailbag.html
```

Or just download `trailbag.html` and open it — it's fully self-contained.

---

## How It Works

### Ingredients

Each ingredient stores per-gram nutritional values and a **rehydration ratio** (how many grams of water the ingredient absorbs when rehydrated). A ratio of `2.0` means 100g dry weight requires 200g of water.

Built-in defaults include instant rice, freeze-dried chicken, dehydrated black beans, and tomato powder. You can add, edit, or delete any ingredient.

### Recipes

A recipe is a named collection of ingredients with dry weights in grams. TrailBag computes totals for:

- Dry pack weight (g and oz)
- Water needed for rehydration (g and oz)
- Total calories
- Full macronutrient breakdown

Recipes support a **base servings** count. You can view any recipe scaled to a different number of servings without modifying the base.

### Rankings

The Rankings tab sorts all recipes by **cal/oz** (calories per ounce of dry weight) — the standard backpacker efficiency metric. Top three get 🥇🥈🥉.

---

## Data Format

Import/export uses a simple JSON structure:

```json
{
  "ingredients": [
    {
      "id": "abc123",
      "name": "Instant Rice",
      "rehydrationRatio": 1.5,
      "calPerG": 3.6,
      "fatPerG": 0.005,
      "sodiumPerG": 0.002,
      "carbPerG": 0.79,
      "fiberPerG": 0.01,
      "proteinPerG": 0.07
    }
  ],
  "recipes": [
    {
      "id": "def456",
      "name": "Rice & Chicken Bowl",
      "servings": 1,
      "items": [
        { "ingredientId": "abc123", "grams": 80 }
      ]
    }
  ]
}
```

---

## Tech Stack

- **React 18** (via CDN, no bundler)
- **Babel Standalone** for in-browser JSX transpilation
- **localStorage** for persistence
- Zero external UI libraries — all styling is inline React

---

## License

MIT
