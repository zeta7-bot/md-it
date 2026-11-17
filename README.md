# md-it

Apa pun jadi Markdown — semuanya di dalam browser.

Tool satu halaman untuk mengubah dokumen menjadi Markdown yang rapi, supaya gampang ditempel sebagai konteks ke AI agent. Tidak ada backend, tidak ada upload: file dibaca dan dikonversi di perangkat sendiri.

**Demo:** https://zeta7-bot.github.io/md-it/

## Format yang didukung

| Format | Cara kerja |
| --- | --- |
| `.pdf` | pdf.js, teks diambil per halaman dengan pemisah `<!-- halaman N -->` |
| `.docx` | mammoth.js (HTML) → Turndown (Markdown), tabel ikut dikonversi |
| `.xlsx` / `.xls` | SheetJS, setiap sheet jadi tabel Markdown dengan heading `## Nama Sheet` |
| `.csv` | parser CSV sederhana → tabel Markdown |
| `.html` / `.htm` | Turndown, termasuk tabel dan tautan |
| `.txt` / `.md` / `.json` | apa adanya, JSON dirapikan ke code block |
| tempelan teks/HTML | terdeteksi otomatis, HTML dikonversi, teks dibiarkan |

Gambar dan scan **tidak** didukung — OCR sengaja dilewati agar halaman tetap ringan. PDF hasil scan akan menghasilkan output kosong.

## Fitur

- Tarik-lepas atau pilih beberapa file sekaligus
- Opsi gabung semua hasil jadi satu `.md` (berguna untuk konteks agent)
- Salin ke clipboard atau unduh sebagai `.md`
- 100% statis: cocok untuk GitHub Pages, tanpa kuota Actions

## Menjalankan lokal

```bash
python3 -m http.server 8000
# buka http://localhost:8000
```

Membuka `index.html` langsung lewat `file://` juga bisa.

## Catatan keterbatasan

- PDF dua kolom dan PDF dengan banyak tabel akan kehilangan struktur; urutan teks mengikuti posisi vertikal.
- `pptx`, audio, dan video tidak didukung.
- Semua library dimuat dari CDN, jadi butuh koneksi internet.

## Lisensi

MIT
