[README.md](https://github.com/user-attachments/files/29448413/README.md)

#  MusicCloud

> A SoundCloud-style Web3 music platform where every artist gets equal time in the spotlight — no follower count, no pay-to-play.

**[→ Open the app](https://musiccloudmp3.com)** · **[→ Project page](https://thecathousemp3.github.io/musiccloud)**

---

## What is this?

MusicCloud is a music sharing and discovery platform built on Web3 principles. Wallet = your account. No email. No password. Upload tracks, mint them as NFTs on Base L2, and get discovered — guaranteed.

## Key features

| Feature | Description |
|---|---|
| 🔁 **Fair Discovery** | Discover feed rotates by time since last featured, not follower count |
| 📈 **Anti-monopoly Trending** | Max 2 tracks per artist on the chart, no matter how popular |
| 🔷 **NFT Minting** | ERC-1155 editions on Base L2 · 97% to the artist · 3% platform fee |
| 👛 **Wallet Auth** | Any EVM wallet works (MetaMask, Rainbow, Coinbase) · EIP-6963 |
| 🎧 **Global Audio Player** | Persistent waveform visualizer across every page |
| 💬 **Timestamp Comments** | Click the waveform to comment at that exact moment |
| 📻 **Live Spaces** | WebRTC voice rooms, straight from the browser |
| 🔔 **Real-time Notifications** | Likes, comments, follows, DMs via server-sent events |
| 🎬 **Video & Voice Memos** | Pro artists can upload MP4 videos and voice memos |
| 🔒 **Private DMs** | Direct messaging between artists and fans |

## How it works

**Discovery algorithm**
```
SELECT * FROM tracks
ORDER BY COALESCE(last_featured_at, created_at) ASC, plays_count ASC
```
Every track gets a turn. New artists with zero followers appear before established artists who were just featured.

**Trending algorithm**
```
score = plays×0.5 + likes×2 + comments×1.5 + reposts×1
cap   = max 2 tracks per artist
```

**NFT minting**
Tracks are listed as ERC-1155 editions. Fans buy directly from the artist profile on Base L2. Secondary royalties route back to the creator automatically.

## Tech stack

- **Frontend** — React + Vite + React Query
- **Backend** — Express 5 + Drizzle ORM + PostgreSQL
- **Auth** — express-session + bcryptjs (wallet signature verification)
- **Storage** — Cloudflare R2
- **Chain** — Base L2 (ERC-1155, EIP-6963, window.ethereum)
- **Realtime** — Server-sent events (SSE)
- **Comms** — WebRTC mesh for Spaces

## Live

**[musiccloudmp3.com](https://musiccloudmp3.com)**

NFT contract on Base L2: [`0xbc72d3e4e82a5faa6cd58316c7da1747d82dd019`](https://basescan.org/address/0xbc72d3e4e82a5faa6cd58316c7da1747d82dd019)

---

*Built by [@thecathousemp3](https://github.com/thecathousemp3)*
