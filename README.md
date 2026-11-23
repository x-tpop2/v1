# SIGAP BRANTAS — PWA Laporan Lapangan BBWS Brantas (v2.6.1)
## Jalankan lokal (kamera & GPS aktif)
  python -m http.server 8080   →  http://localhost:8080
  (membuka index.html via file:// membatasi kamera/GPS di sebagian browser)
## Deploy GitHub Pages
1. Repo root: index.html, manifest.json, sw.js, icons/icon-192.png, icons/icon-512.png
   (ikon PNG bisa diunduh dari aplikasi: Sistem → Deploy GitHub → Unduh ikon)
2. Settings → Pages → Deploy from branch → main / root.
3. Buka https://USER.github.io/REPO/ → instal PWA.
## Struktur repo
apps/web/  index.html manifest.json sw.js icons/
gas/       Code.gs Drive.gs Sheet.gs Config.gs
supabase/  migrations/001_init.sql functions/login/
docs/      arsitektur.md sop-petugas.md
## Integrasi produksi
- GAS Web App: deploy "Execute as me / Anyone"; SECRET di Script Properties.
- Supabase: jalankan 001_init.sql; edge function login menyetel klaim uid/role/di.
- Spreadsheet: LAPORAN (metadata+link), MASTER_PEGAWAI, DRIVE_POOL, CONFIG.
- Drive: 3 pool; rotasi otomatis saat usage >= 90%.
- Preview: lh3.googleusercontent.com/d/FILEID=w1600 (hemat kuota viewer).
## Skala 1.232+ petugas
Pagination 24 baris, lazy-load foto, index DB, RLS per scope,
batch appendRows + LockService, retry backoff, SW cache shell.