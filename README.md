# Dayalima Brand Hub

Landing page internal untuk **brand.dayalima.app** — satu sumber resmi aset brand (logo, template, company profile, dan panduan) yang bisa diakses oleh seluruh business unit Dayalima Group.

Static site, tanpa backend. Semua kode ada di `index.html` (HTML + CSS + JS inline, tidak ada file terpisah).

## Struktur file

```
index.html                          → halaman utama
logo-color.png                      → logo utama, untuk latar terang
logo-white.png                      → logo putih, untuk latar merah/gelap
Dayalima-Brand-Guideline.png        → cuplikan panduan brand internal (1 halaman)
Dayalima-Company-Profile-2026.pdf   → company profile terbaru
Dayalima-Template-Presentasi.pptx   → master template slide
Dayalima-Brand-Kit.zip              → bundel semua file di atas jadi satu (untuk tombol "Unduh Brand Kit")
```

Semua path aset di `index.html` bersifat **relatif** — file-file ini wajib berada di root repo yang sama dengan `index.html` agar logo, preview, dan tombol download tetap berfungsi.

## Deploy ke GitHub Pages

1. Push seluruh file di atas ke root repo (branch `main`).
2. Repo → **Settings → Pages** → Source: branch `main`, folder `/root` → Save.
3. Custom domain: isi `brand.dayalima.app` di kolom "Custom domain" (GitHub otomatis membuat file `CNAME`).
4. Di DNS provider domain `dayalima.app`, arahkan:
   ```
   Type: CNAME
   Name: brand
   Value: <username>.github.io
   ```
5. Aktifkan **Enforce HTTPS** setelah DNS propagasi (biasanya 10–30 menit).

## Cara update aset

Karena semua path relatif dan mengacu ke nama file, update cukup dengan **replace file lama dengan nama yang sama**, lalu commit & push — tidak perlu menyentuh `index.html`.

Pengecualian: `Dayalima-Brand-Kit.zip` **tidak otomatis ter-update**. Setiap kali salah satu aset di dalamnya berubah (logo baru, company profile edisi baru, dst), file ZIP ini harus di-generate ulang secara manual dan di-replace juga.

## Kerangka isi halaman

| Section | ID | Isi |
|---|---|---|
| Header | — | Logo + navigasi + tombol "Unduh Semua" (download ZIP) |
| Hero | `#top` | Headline, CTA unduh brand kit & lihat panduan |
| Identitas Brand | `#identitas` | Palet warna (rasio 60/30/10) & tipografi |
| Logo Kit | `#logo-kit` | Logo utama & logo putih, masing-masing dengan tombol unduh |
| Template & Dokumen | `#dokumen` | Template PPTX, Company Profile PDF, Panduan Brand PNG |
| Rekan Desain | `#vendor` | Info vendor desain **Pameo** — link portofolio & form request masih placeholder, lihat catatan di bawah |
| Panduan Lengkap | `#panduan` | Preview panduan brand + ringkasan aturan pakai |
| CTA / Kontak | `#kontak` | Kontak tim Marketing |
| Footer | — | Navigasi ulang, alamat kantor, kontak, copyright |

## Belum final — perlu ditindaklanjuti

- **Link Pameo** — dua tombol di section `#vendor` ("Lihat Portofolio Pameo" & "Ajukan Request Desain") masih `href="#"`. Ganti begitu link/form resminya tersedia.
- **Font TStar Pro Bold** — belum ada lisensi web font, saat ini di-substitusi dengan **Oswald** (Google Fonts) yang punya karakter serupa (kondensed, bold, uppercase). Ganti `font-family` di CSS bila lisensi TStar Pro sudah didapat.
- **Struktur per-BU** — saat ini semua aset bersifat generik untuk seluruh Dayalima Group. Kalau tiap BU (DaDI, DayaSkill, DayaCircle, Klobility, Klob) butuh template/aset tersendiri, perlu didiskusikan apakah dibuat sub-halaman terpisah atau filter di halaman yang sama.

## Brand tokens (referensi cepat untuk dev)

```css
--red:        #A21F21;  /* primer, 60% */
--gray-200:   #D9D9D9;  /* sekunder, 30% */
--yellow:     #FFCC05;  /* aksen, 10% */
--ink:        #201C1C;  /* teks/latar gelap */
```

Headline: **TStar Pro Bold** (fallback: Oswald) · Body: **Montserrat**

---
© 2026 Dayalima Group. Internal use only.
