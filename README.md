<p align="center">
  <img src="https://img.shields.io/badge/Python-3.9+-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/Streamlit-1.30+-FF4B4B?style=for-the-badge&logo=streamlit&logoColor=white" alt="Streamlit">
  <img src="https://img.shields.io/badge/Google%20Sheets-API%20v4-34A853?style=for-the-badge&logo=googlesheets&logoColor=white" alt="Google Sheets">
  <img src="https://img.shields.io/badge/YouTube-API%20v3-FF0000?style=for-the-badge&logo=youtube&logoColor=white" alt="YouTube">
  <img src="https://img.shields.io/badge/Supermetrics-Enterprise-6C5CE7?style=for-the-badge" alt="Supermetrics">
</p>

<h1 align="center">📊 SocialPulse Analytics</h1>

<p align="center">
  <strong>Unified Social Media Intelligence Platform</strong><br>
  <em>Automated analytics pipeline for Instagram, Facebook & YouTube — delivering structured insights to Google Sheets</em>
</p>

<p align="center">
  <a href="#-overview">Overview</a> •
  <a href="#-features">Features</a> •
  <a href="#-architecture">Architecture</a> •
  <a href="#-platforms">Platforms</a> •
  <a href="#-metrics">Metrics</a> •
  <a href="#-tech-stack">Tech Stack</a> •
  <a href="#-demo">Demo</a>
</p>

---

## 🎯 Overview

**SocialPulse Analytics** is an enterprise-grade social media analytics dashboard that automates the entire data lifecycle — from extraction to aggregation — across the three largest social platforms. Built with Streamlit, it provides a clean, intuitive interface for social media analysts and campaign managers to generate comprehensive performance reports without writing a single line of code.

> **🔒 Note:** This is a showcase repository. The full source code is maintained in a private repository.

---

## ✨ Features

<table>
<tr>
<td width="50%">

### 📸 Instagram Analytics
- Post-level data extraction (likes, comments, media)
- Profile engagement rate computation
- Follower-normalized metrics
- Automatic date-range chunking for large datasets

</td>
<td width="50%">

### 📘 Facebook Analytics
- Reactions breakdown (love, wow, haha, sad, angry)
- Share tracking and virality metrics
- Page follower growth correlation
- Assembly constituency-level segmentation

</td>
</tr>
<tr>
<td width="50%">

### 🎬 YouTube Analytics
- Channel statistics (subscribers, total views)
- Video-level performance metrics
- Hashtag and tag extraction
- Playlist-based comprehensive video discovery

</td>
<td width="50%">

### 📊 Unified Reporting
- Google Sheets integration (read input → write output)
- Raw data + aggregated summary sheets
- Per-post and per-profile engagement calculations
- Date-stamped report generation

</td>
</tr>
</table>

---

## 🏗️ Architecture

```
                    ┌─────────────────────────┐
                    │    Streamlit Dashboard   │
                    │    (Web Interface)       │
                    └────────────┬────────────┘
                                 │
                    ┌────────────▼────────────┐
                    │   Platform Router        │
                    │ Instagram│Facebook│YouTube│
                    └────┬──────┬──────┬──────┘
                         │      │      │
              ┌──────────▼┐  ┌─▼──────▼──────────┐
              │Supermetrics│  │  YouTube Data API  │
              │  API       │  │       v3           │
              └──────┬─────┘  └────────┬───────────┘
                     │                 │
              ┌──────▼─────────────────▼───────┐
              │     Data Processing Engine      │
              │  • Chunked fetching             │
              │  • Metric computation           │
              │  • Engagement normalization     │
              │  • Date filtering & aggregation │
              └──────────────┬─────────────────┘
                             │
              ┌──────────────▼─────────────────┐
              │     Google Sheets API v4        │
              │  • Read profile/page lists      │
              │  • Write raw data sheets        │
              │  • Write aggregated reports     │
              └────────────────────────────────┘
```

---

## 📱 Platforms Supported

| Platform | Data Source | Key Metrics |
|----------|-----------|-------------|
| <img src="https://img.shields.io/badge/-Instagram-E4405F?logo=instagram&logoColor=white" alt="Instagram"> | Supermetrics `IGPD2` | Likes, Comments, Engagement Rate, Follower Count |
| <img src="https://img.shields.io/badge/-Facebook-1877F2?logo=facebook&logoColor=white" alt="Facebook"> | Supermetrics `FBPD` | Reactions, Shares, Comments, Page Followers |
| <img src="https://img.shields.io/badge/-YouTube-FF0000?logo=youtube&logoColor=white" alt="YouTube"> | YouTube Data API v3 | Views, Likes, Comments, Subscribers, Video Count |

---

## 📊 Metrics Computed

### Engagement Metrics
| Metric | Formula | Platforms |
|--------|---------|-----------|
| **Interaction per Post** | Likes + Comments (+ Shares for FB) | IG, FB |
| **Engagement per Post** | (Interactions / Followers) × 100 | IG, FB |
| **Avg Engagement** | Total Engagement / Total Posts | IG, FB |
| **Shares per 1000 Followers** | Shares / (Followers / 1000) | FB |
| **Reactions per 1000 Followers** | Reactions / (Followers / 1000) | FB |

### Aggregation Metrics
| Metric | Description | Platforms |
|--------|-------------|-----------|
| **Total Posts** | Count of posts in date range | IG, FB, YT |
| **Total Likes** | Sum of likes across all posts | IG, FB, YT |
| **Total Comments** | Sum of comments across all posts | IG, FB, YT |
| **Likes per Post** | Average likes per post | IG, FB |
| **Comments per Post** | Average comments per post | IG, FB |
| **Unique Videos** | Distinct videos published | YT |
| **Sum of Views** | Aggregate views in period | YT |

---

## 🔄 Data Pipeline Flow

```
1️⃣  INPUT         →  Google Sheets (Profile/Page URLs, metadata)
2️⃣  EXTRACTION    →  Supermetrics API / YouTube API (raw social data)
3️⃣  PROCESSING    →  Date filtering, metric computation, engagement calc
4️⃣  AGGREGATION   →  Group-by-profile summaries, per-post averages
5️⃣  OUTPUT        →  Google Sheets (raw_data + agg_data worksheets)
```

---

## 🛠️ Tech Stack

| Layer | Technology | Purpose |
|-------|-----------|---------|
| **Frontend** | [Streamlit](https://streamlit.io/) | Interactive web dashboard |
| **Data Engine** | [Pandas](https://pandas.pydata.org/) + [NumPy](https://numpy.org/) | Data processing & computation |
| **Instagram/FB API** | [Supermetrics](https://supermetrics.com/) | Enterprise social data extraction |
| **YouTube API** | [YouTube Data API v3](https://developers.google.com/youtube/v3) | Channel & video analytics |
| **Storage** | [Google Sheets API v4](https://developers.google.com/sheets/api) | Input/Output data layer |
| **Sheets Client** | [pygsheets](https://pygsheets.readthedocs.io/) + [gspread](https://gspread.readthedocs.io/) | Sheets read/write operations |
| **Auth** | [Google OAuth 2.0](https://developers.google.com/identity) | Service account authentication |
| **CI/CD** | [GitHub Actions](https://github.com/features/actions) | Automated testing & validation |
| **Deployment** | [Streamlit Cloud](https://streamlit.io/cloud) | Production hosting |

---

## 🎨 Demo

### Dashboard Navigation
The application features a sidebar-driven navigation with three main modules:

| Step | Action |
|------|--------|
| 1 | Select platform (Instagram / Facebook / YouTube) from sidebar |
| 2 | Enter Google Sheet ID containing profile data |
| 3 | Select specific worksheet and date range |
| 4 | Click "Fetch Data" to trigger the pipeline |
| 5 | Raw and aggregated reports auto-populate in the Sheet |

### Output Example
Each run creates **two new worksheets** in your Google Sheet:
- **`[platform]_raw_data`** — Every post with full metrics
- **`[platform]_agg_data`** — Per-profile aggregated summary

---

## 🔐 Security & Configuration

- 🔑 All API keys stored via **Streamlit Secrets** (never in code)
- 🛡️ GCP Service Account with **least-privilege** Sheets API scope
- 🔒 Credentials written to **ephemeral temp files** (auto-deleted)
- ✅ CI/CD includes **Bandit** security scanning & **Safety** dependency audits
- 📋 `.gitignore` blocks all credential files from version control

---

## 📈 Performance & Scalability

| Feature | Implementation |
|---------|---------------|
| **Large date ranges** | Auto-chunked into 10-day (FB) or 365-day (IG) windows |
| **API rate limits** | Sequential processing with error handling per account |
| **Data volume** | Supports up to 100,000 rows per Supermetrics query |
| **Error resilience** | Graceful degradation — skips failed accounts, continues pipeline |

---

## 🚀 Deployment

The application is designed for **Streamlit Cloud** deployment:

1. Connect GitHub repository to Streamlit Cloud
2. Configure secrets in the Streamlit Cloud dashboard
3. Set `app.py` as the main file
4. Deploy with one click

---

## 📫 Contact

For inquiries about this project, please reach out to the development team.

---

<p align="center">
  <strong>Built with ❤️ using Python, Streamlit & Google APIs</strong>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Status-Production-brightgreen?style=flat-square" alt="Status">
  <img src="https://img.shields.io/badge/Maintained-Yes-blue?style=flat-square" alt="Maintained">
</p>

