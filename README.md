# Pertemuan 13 - Debugging dan Testing

## Identitas
- Nama: Zakiyatus Salsabila
- NIM: 0225
- Kelas: Pendidikan Matematika

## 1. Deskripsi Program
Program ini digunakan untuk menghitung rata-rata nilai, menentukan status kelulusan, dan mencari nilai tertinggi dari sekumpulan data nilai.

Pada praktikum ini dilakukan proses debugging dan testing untuk menemukan kesalahan pada program awal, memperbaiki kesalahan, dan menguji kembali program menggunakan lima test case.

## 2. Output Aktual Program Awal

Hasil ketika program awal dijalankan:

```text
Rata-rata: 60.0
Status 60: Tidak lulus
Tertinggi: 0
```

Hasil tersebut belum sesuai dengan hasil yang diharapkan.

## 3. Test Case

| ID | Target | Input | Expected | Actual Awal | Status |
|---|---|---|---|---|---|
| T1 | Rata-rata | [80,60,90,70] | 75.0 | 60.0 | FAIL |
| T2 | Rata-rata | [100,80] | 90.0 | 36.0 | FAIL |
| T3 | Status | 60 | Lulus | Tidak lulus | FAIL |
| T4 | Status | 59 | Tidak lulus | Tidak lulus | PASS |
| T5 | Tertinggi | [80,60,90,70] | 90 | 0 | FAIL |

## 4. Bug Report

### B01 - Kesalahan Menghitung Rata-rata
- Gejala: Hasil rata-rata tidak sesuai.
- Test case: T1 dan T2.
- Lokasi: Fungsi `hitung_rata_rata()`.
- Akar penyebab: Program selalu membagi jumlah nilai dengan angka 5, padahal jumlah data bisa berbeda.
- Perbaikan: Mengganti angka 5 dengan `len(nilai)`.

### B02 - Kesalahan Menentukan Status
- Gejala: Nilai 60 dinyatakan tidak lulus.
- Test case: T3.
- Lokasi: Fungsi `status()`.
- Akar penyebab: Penggunaan operator `>` menyebabkan nilai 60 tidak memenuhi kondisi.
- Perbaikan: Mengganti operator `>` menjadi `>=`.

### B03 - Kesalahan Mencari Nilai Tertinggi
- Gejala: Program menghasilkan nilai 0.
- Test case: T5.
- Lokasi: Fungsi `nilai_tertinggi()`.
- Akar penyebab: Operator perbandingan terbalik, yaitu menggunakan `<`.
- Perbaikan: Mengganti operator `<` menjadi `>` dan mengawali nilai tertinggi dari elemen pertama.

## 5. Retest Setelah Perbaikan

| ID | Expected | Actual | Status |
|---|---|---|---|
| T1 | 75.0 | 75.0 | PASS |
| T2 | 90.0 | 90.0 | PASS |
| T3 | Lulus | Lulus | PASS |
| T4 | Tidak lulus | Tidak lulus | PASS |
| T5 | 90 | 90 | PASS |

Hasil pengujian menunjukkan bahwa seluruh test case berhasil mendapatkan status PASS.

## 6. Cara Menjalankan Program

Jalankan program awal:

```bash
python3 program_awal.py
```

Jalankan program setelah diperbaiki:

```bash
python3 praktik_4_debugging.py
```

## 7. Refleksi

Teknik debugging yang paling membantu adalah menjalankan program menggunakan beberapa test case dan membandingkan hasil aktual dengan hasil yang diharapkan.

Dengan cara tersebut, kesalahan dapat ditemukan berdasarkan hasil pengujian. Setelah mengetahui penyebabnya, kode diperbaiki dan diuji kembali.

Dari praktikum ini saya memahami bahwa debugging berguna untuk menemukan dan memperbaiki kesalahan, sedangkan testing digunakan untuk memastikan program berjalan sesuai dengan hasil yang diharapkan.