# QR Stüdyo

Tarayıcıda çalışan, build adımı olmayan tek dosyalık QR kod stüdyosu. Üç mod: düz QR, kartvizit, föy/plaka.

## Özellikler

**Üç ayrı mod:**

1. **Düz QR** — URL, vCard, Metin, Email, Telefon, SMS, WiFi. Renk + boyut (mm) + hata düzeltme seviyesi. PNG / JPG / SVG / PDF (vektörel).
2. **Kartvizit (83 × 51 mm)** — Tam vCard formu, logo yükleme, 8 renk teması, custom renk seçici (BG, yazı, vurgu, QR). Yatay baskı için tam mm boyutunda PDF.
3. **Föy / Plaka (130 × 160 mm)** — QR + başlık + açıklama + logo. Kafe menüsü, WiFi paylaşımı, rezervasyon vs. için.

**Ortak:**

- Anlık önizleme
- Logo yükleme (FileReader, sunucuya bir şey gitmiyor)
- Karanlık / aydınlık tema (kalıcı)
- Tüm modlarda vektörel veya 4× çözünürlüklü PNG export

## Yerel Çalıştırma

`index.html` dosyasını tarayıcıda aç, hepsi bu.

```bash
# veya local server ile
python3 -m http.server 8000
# http://localhost:8000
```

## Deploy

### Netlify

Repo'yu Netlify'a bağla. `netlify.toml` zaten ayarlı (build command yok, publish dir `.`).

Veya CLI ile:

```bash
npx netlify deploy --prod --dir=.
```

### Vercel

```bash
npx vercel --prod
```

`vercel.json` hazır.

### GitHub Pages

Settings → Pages → Source: `main` / root.

## Veri Gizliliği

Hiçbir veri sunucuya gitmez — tüm QR üretimi, render ve PDF tarayıcıda olur. CDN'den sadece üç JS kütüphanesi yüklenir:

- [qrcode-generator](https://github.com/kazuhikoarase/qrcode-generator) — QR matrisi
- [jsPDF](https://github.com/parallax/jsPDF) — PDF üretimi
- [html2canvas](https://github.com/niklasvh/html2canvas) — kartvizit/föy görselini yakalama

## Lisans

MIT
