# MashPass 🎓

> The campus connection app — date, study, vibe, network, or just make friends. No logins, no swiping nonsense.

![MashPass](https://img.shields.io/badge/MashPass-Campus%20Vibes-ff6b6b?style=for-the-badge&logoColor=white)
![HTML](https://img.shields.io/badge/HTML-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS](https://img.shields.io/badge/CSS-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![Supabase](https://img.shields.io/badge/Supabase-3ECF8E?style=for-the-badge&logo=supabase&logoColor=white)

---

## What is MashPass?

MashPass is a student connection platform built for campus life. Unlike typical dating apps, MashPass lets students connect across multiple vibes:

| Vibe | What it means |
|------|--------------|
| 💕 Date | Romantic connections |
| 📚 Study | Study partners & academic help |
| 🤝 Friends | Just making genuine friends |
| 💼 Network | Professional & career connections |
| 🎵 Vibe | Hang out, explore, no labels |

Students drop a profile card with their photo, bio, university, and contact details. Others can **Mash** to reveal contact info, or **Pass** to skip. No accounts, no passwords.

---

## Features

- 🪪 **No login required** — drop a card and go
- 📸 **Photo upload** — straight from your device
- 🎯 **Multi-vibe profiles** — you're not just one thing
- 🔍 **Filter by vibe** — find exactly who you're looking for
- 💌 **Matches page** — saved connections with contact details
- ☁️ **Supabase backend** — profiles persist across devices
- 📱 **Mobile friendly** — works on any screen
- 🌍 **Open to all SA campuses** — UCT, Wits, Stellenbosch, CPUT, UKZN, NWU and more

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | HTML, CSS, Vanilla JavaScript |
| Database | Supabase (PostgreSQL) |
| Storage | Supabase Storage (photos) |
| Hosting | GitHub Pages / Any static host |

No frameworks. No build tools. No npm. Just open the file and it works.

---

## Getting Started

### 1. Clone the repo

```bash
git clone https://github.com/YOUR_USERNAME/mashpass.git
cd mashpass
```

### 2. Set up Supabase

1. Go to [supabase.com](https://supabase.com) and create a free account
2. Create a new project (pick the region closest to you)
3. In the Supabase dashboard go to **SQL Editor → New Query**
4. Paste and run the contents of [`mashpass_setup.sql`](./mashpass_setup.sql)
5. Go to **Project Settings → API** and copy your:
   - **Project URL** (looks like `https://abcxyz.supabase.co`)
   - **anon / public key** (starts with `eyJ...`)

### 3. Add your keys to the HTML

Open `mashpass.html` in any text editor and find these two lines near the bottom:

```js
const SUPABASE_URL = 'YOUR_SUPABASE_URL';
const SUPABASE_KEY = 'YOUR_SUPABASE_ANON_KEY';
```

Replace the placeholder values with your real keys.

### 4. Open and go

Open `mashpass.html` in your browser — that's it. No server needed.

---

## Deploying to GitHub Pages

1. Push your code to GitHub
2. Go to your repo → **Settings → Pages**
3. Under **Source** select `main` branch and `/ (root)`
4. Click **Save** — your site will be live at:

```
https://YOUR_USERNAME.github.io/mashpass
```

---

## Is it safe to commit the Supabase key?

**Yes — the anon/public key is designed to be public.** Supabase's security model relies on **Row Level Security (RLS)** policies on the database, not on hiding the anon key. The SQL setup file already enables RLS on the `students` table.

```js
// ✅ Safe to commit — this is the public anon key
// 🔒 Security is enforced by Supabase Row Level Security
// ❌ NEVER commit your service_role key — keep that off GitHub
const SUPABASE_URL = 'https://your-project.supabase.co';
const SUPABASE_KEY = 'eyJ...your-anon-key...';
```

The key that must **never** be shared is the `service_role` key — that one bypasses all security and lives only in your Supabase dashboard.

---

## Project Structure

```
mashpass/
│
├── mashpass.html        # The entire app — HTML, CSS, and JS in one file
├── mashpass_setup.sql   # Run this in Supabase SQL Editor to set up the database
└── README.md            # You're reading it
```

---

## Database Schema

The `students` table in Supabase:

```sql
id          uuid        primary key
created_at  timestamptz default now()
name        text        not null
age         int
uni         text        not null
course      text
year        text
bio         text
vibes       text[]      array of vibes e.g. {date, study, friends}
whatsapp    text
insta       text
email       text
linkedin    text
photo_url   text        public URL from Supabase Storage
emoji       text        fallback if no photo
```

---

## Roadmap

- [ ] Profile deletion (via secret code on creation)
- [ ] Search by university
- [ ] Report / flag a profile
- [ ] Dark / light mode toggle
- [ ] Share a profile link
- [ ] PWA support (installable on phone)

---

## Contributing

Pull requests are welcome. For major changes please open an issue first to discuss what you'd like to change.

1. Fork the repo
2. Create your branch (`git checkout -b feature/cool-thing`)
3. Commit your changes (`git commit -m 'Add cool thing'`)
4. Push to the branch (`git push origin feature/cool-thing`)
5. Open a Pull Request

---

## License

[MIT](./LICENSE) — free to use, modify, and share.

---

## Built with ❤️ for SA students

MashPass was built for students across South African campuses who want real connections — not just matches. Whether you're trying to survive finals week, find your people, build your network, or just vibe — this is your space.

*Drop your card. Find your vibe. MashPass.* 🎓
