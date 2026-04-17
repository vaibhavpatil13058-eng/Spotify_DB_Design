# 🎵 Spotify Database System

A MySQL-based database design that replicates the core functionality of Spotify, including music streaming, podcasts, playlists, and user interactions.

---

## 🚀 Features

* 🎶 Manage songs, albums, and artists
* 🎙️ Support for podcasts and episodes
* 🎥 Audio + Video media handling
* ❤️ Like songs and podcast episodes
* 📂 Create and manage playlists
* ▶️ Track play history
* ⚙️ User playback preferences (Audio/Video mode)

---

## 🧱 Database Design

The system is built using a **relational database model (MySQL)** with proper normalization and foreign key constraints.

### Main Entities:

* USERS
* ARTISTS
* ALBUMS
* SONGS
* PODCASTS
* EPISODES
* MEDIA_FILES
* PLAYLISTS

---

## 🔗 Relationships

* One Artist → Many Albums
* One Album → Many Songs
* One Podcast → Many Episodes
* Many Songs ↔ Many Playlists
* Many Episodes ↔ Many Playlists
* Media files linked to songs and episodes

---

## 🎬 Media Handling

Supports both **audio and video streaming**:

* Screen ON → Video playback 🎥
* Screen OFF → Audio playback 🎧

Media is stored separately in the `MEDIA_FILES` table and linked using mapping tables.

---

## 📊 Sample Queries

### 🔍 Fetch Songs with Artist & Album

```sql
SELECT s.Title, a.Title AS Album, ar.Name AS Artist
FROM SONGS s
JOIN ALBUMS a ON s.AlbumID = a.AlbumID
JOIN ARTISTS ar ON a.ArtistID = ar.ArtistID;
```

---

### ❤️ Get Liked Songs

```sql
SELECT s.Title
FROM LIKED_SONGS ls
JOIN SONGS s ON ls.SongID = s.SongID
WHERE ls.UserID = 1;
```

---

### 📂 Songs in Playlist

```sql
SELECT s.Title
FROM PLAYLIST_SONGS ps
JOIN SONGS s ON ps.SongID = s.SongID
WHERE ps.PlaylistID = 1;
```

---

### 📈 Most Played Songs

```sql
SELECT s.Title, COUNT(*) AS PlayCount
FROM PLAY_HISTORY ph
JOIN SONGS s ON ph.SongID = s.SongID
GROUP BY s.SongID
ORDER BY PlayCount DESC;
```

---

## ⚙️ Technologies Used

* MySQL
* SQL (DDL & DML)
* Relational Database Design

---

## 🧠 Key Concepts

* Normalization (3NF)
* Foreign Key Constraints
* Many-to-Many Relationships
* Junction Tables
* Media Abstraction (Audio/Video)

---

## 📁 Project Structure

```
spotify-db/
│── schema.sql
│── queries.sql
│── README.md
```

---

## 🏁 Getting Started

1. Clone the repository
2. Open MySQL
3. Run the schema file:

```sql
SOURCE schema.sql;
```

---

## 🔮 Future Improvements

* Recommendation system
* User subscription billing
* Offline downloads
* Real-time analytics

---

## 📌 Author

* Vaibhav Patil

---

## ⭐ Acknowledgement

This project is created for learning database design and understanding how real-world streaming platforms like Spotify manage data.

