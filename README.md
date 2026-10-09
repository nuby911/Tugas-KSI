# Web Dummy Asisten Kantin Polinela · Risiko AI/LLM & Mitigasi

Proyek implementasi web dummy untuk mata kuliah **Keamanan Sistem Informasi (PMI 1522)** Minggu 6: *Risiko AI/LLM dan Prompt Injection*.

## Identitas Mahasiswa
- **Nama:** Rubby Ibnu Anantara
- **NPM:** 24781025
- **Kelas:** MI-5A
- **Program Studi:** D-III Manajemen Informatika
- **Institusi:** Politeknik Negeri Lampung (POLINELA)
- **Repository GitHub:** https://github.com/nuby911/Tugas-KSI
- **Kasus Uji:** LIVE-1 (Chatbot Kantin Kampus · Direct Prompt Injection)

---

## 🎯 Tujuan Proyek
Membuktikan secara empiris kerentanan **Direct Prompt Injection** pada asisten cerdas berbasis LLM ketika aturan sistem dan input pengguna digabungkan tanpa hierarki peran (flat prompt), serta menerapkan mitigasi pertahanan berlapis di luar model:
1. **Instruction Hierarchy:** Memisahkan instruksi sistem dengan input pengguna menggunakan pembatas data yang ketat (`JSON.stringify` / delimitasi kontekstual).
2. **Output Validation & Enforcement:** Memeriksa dan memvalidasi respons model di lapisan aplikasi sebelum ditampilkan ke pengguna.
3. **Least Privilege & Revocation of Privileged Actions:** Mencabut fungsi atau izin penerbitan voucher diskon dari wewenang asisten cerdas dan mengembalikannya ke staf kasir resmi.

---

## 📁 Struktur Berkas

| Berkas | Deskripsi |
| :--- | :--- |
| `index.html` | Portal web aplikasi terpadu (Unified Web App) dengan switcher Mode Rentan vs Mode Aman interaktif. |
| `24781025-kantin-voucher-rentan.html` | Berkas mandiri versi rentan (memenuhi kontrak `window.asisten`). |
| `24781025-kantin-voucher-aman.html` | Berkas mandiri versi aman (memenuhi kontrak `window.asisten` dengan mitigasi). |
| `24781025-LIVE-1-rentan-log.json` | Log rekaman pengujian LLM asli versi rentan (format `P06-WEB-DUMMY`). |
| `24781025-LIVE-1-aman-log.json` | Log rekaman pengujian LLM asli versi aman (format `P06-WEB-DUMMY`). |
| `P06-backup-24781025.json` | Berkas backup praktikum resmi 100% lengkap (identitas, 4 lab, 10 studi kasus, web dummy). |

---

## 🛡️ Kontrak Teknis
Setiap halaman mengimplementasikan fungsi standar:
```javascript
window.asisten = async function (pesan, konteks, model) {
  // model: async (prompt) => text
  return {
    balasan: "Teks jawaban",
    aksi: [/* daftar aksi tool */]
  };
};
```

---

## 🚀 Panduan Deploy ke Netlify
1. Buka browser dan kunjungi [app.netlify.com/drop](https://app.netlify.com/drop) (pastikan sudah login akun Netlify).
2. Seret (*drag & drop*) folder `web-dummy-kantin` ke area unggah Netlify Drop.
3. Setelah proses unggah selesai, klaim situs dan salin URL publik yang dihasilkan (contoh: `https://kantin-ai-rubby.netlify.app/`).
4. Akses URL tersebut untuk memastikan halaman `index.html`, `/24781025-kantin-voucher-rentan.html`, dan `/24781025-kantin-voucher-aman.html` berjalan normal via HTTPS.
