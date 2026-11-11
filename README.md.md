# WargaHub P04 - UX, RecyclerView, Fragment, dan Navigasi

## Identitas Mahasiswa
- **Nama:** Riyo Wijaya
- **NIM:** 240104040160
- **Mata Kuliah:** Praktikum Pemrograman Mobile (PTI23043) — 1 SKS
- **Semester / Pertemuan:** Semester V / Pertemuan 4 (Praktikum 04)
- **Dosen Pengampu:** Muhayat, M.IT

## Spesifikasi Lingkungan & Perangkat Uji
- **IDE:** Android Studio
- **Bahasa & UI:** Kotlin, XML Views, ViewBinding, Jetpack Navigation Component
- **Package Name:** `id.antasari.p04.wargahub`
- **Konfigurasi SDK:** `minSdk = 26`, `compileSdk = 37`, `targetSdk = 37`
- **Dependensi Utama:**
  - `androidx.recyclerview:recyclerview:1.4.0`
  - `androidx.fragment:fragment-ktx:1.8.9`
  - `androidx.navigation:navigation-fragment-ktx:2.9.5`
  - `androidx.navigation:navigation-ui-ktx:2.9.5`
- **Perangkat Uji (Emulator):** Medium Phone API 37
- **Orientasi & Aksesibilitas Uji:** Portrait & Landscape, Skala Font Standar & Diperbesar (1,3x–1,5x), serta Pemeriksaan Deskripsi Aksesibilitas Baris (`contentDescription` & `accessibilityLiveRegion`).

## Cara Membuka dan Menjalankan Proyek
1. Buka **Android Studio**, pilih **Open**, lalu arahkan ke folder proyek `WargaHubP04`.
2. Tunggu hingga proses **Gradle Sync** selesai dengan sukses (pastikan koneksi internet aktif pada sinkronisasi pertama untuk mengunduh dependensi yang diperlukan).
3. Pilih perangkat emulator (minimal API 26) atau perangkat fisik Android dengan *USB Debugging* aktif.
4. Klik tombol **Run 'app'** (`Shift + F10`) untuk membangun dan memasang APK ke perangkat.
5. Alternatif melalui terminal proyek:
   - **Windows PowerShell:** `.\gradlew.bat assembleDebug`
   - **macOS / Linux:** `./gradlew assembleDebug`

## Ringkasan Fitur & Batas Data Simulasi
- **Arsitektur Satu Activity & Tiga Fragment:** Menggunakan `MainActivity` sebagai wadah utama yang mengelola `Toolbar` dan `NavHostFragment` untuk menampilkan `HomeFragment` (Beranda), `ListFragment` (Daftar Laporan), serta `DetailFragment` (Rincian Laporan) sesuai `nav_graph.xml`.
- **Daftar 15 Laporan Fiktif (`RecyclerView` & `ListAdapter`):** Menampilkan 15 item laporan lingkungan menggunakan `LaporanAdapter`, `DiffUtil.ItemCallback`, dan `ItemLaporanBinding`.
- **Pengiriman Argumen Navigasi (`Long`) & Back Stack:** Mengirimkan `id` laporan bertipe `Long` melalui `Bundle` (`laporan_id`) ke `DetailFragment`, menggunakan `navigateUp()` untuk kembali tanpa menduplikasi daftar, serta menangani kondisi ID tidak ditemukan (`null`) dengan pesan UI yang aman tanpa *crash*.
- **Simulasi Daftar Kosong & Pemulihan State:** Menyediakan tombol *Uji Daftar Kosong* dan *Tampilkan Data Contoh* yang mempertahankan statusnya saat rotasi layar menggunakan `savedInstanceState`.
- **Batas Data Contoh:** Seluruh data dibentuk secara lokal di memori melalui objek `LaporanContoh` dengan status `"Simulasi"`. Proyek ini belum menerapkan penyimpanan permanen (database lokal maupun pengiriman ke server API).

## Struktur Folder Pengumpulan
```text
P04_240104040160_Riyo_Wijaya/
├── WargaHubP04/                # Source project Android Studio (beserta Gradle Wrapper)
├── docs/
│   └── Laporan_P04.pdf         # Dokumen laporan praktikum lengkap
├── screenshots/
│   ├── 01_beranda.png
│   ├── 02_daftar_laporan.png
│   ├── 03_rincian_laporan.png
│   ├── 04_daftar_kosong.png
│   ├── 05_landscape_font_besar.png
│   └── 06_id_tidak_ditemukan.png
└── README.md                   # Dokumentasi ringkas proyek
```