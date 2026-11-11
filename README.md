# AI4I 2020 — Makine Arızası Tahmini (Makine Öğrenmesi Arasınavı)

**Tuğba Tuana Kaygısız** · Öğrenci No: 2511317024 · MAKÜ Fen-Edebiyat Fakültesi, Veri Bilimi ve Analitiği
Makine Öğrenmesi Dersi Arasınavı · 2026-2027 Güz Yarıyılı · Bilgisayar bölümü (Soru 1–3)

Veri seti: [UCI AI4I 2020 Predictive Maintenance](https://archive.ics.uci.edu/dataset/601/ai4i+2020+predictive+maintenance+dataset) (10.000 kayıt).

## Dosyalar

| Dosya | İçerik |
|---|---|
| [`RAPOR.pdf`](RAPOR.pdf) | Sınav raporu (3 sayfa): Soru 1, 2 ve 3'ün cevapları, tablolar ve grafikler |
| `RAPOR.html` / `RAPOR.md` | Aynı raporun tarayıcıda ve düz metin olarak açılan hâli |
| [`kod/sinav_cozumu.ipynb`](kod/sinav_cozumu.ipynb) | Bütün analiz ve modellerin Python kodu ve çıktıları (Soru 1, 2, 3 sırasıyla) |
| `kod/sinav_cozumu.html` | Defterin Python gerektirmeden açılan hâli |
| `kod/data/ai4i2020.csv` | Veri seti |
| `ciktilar/` | Defterin ürettiği bütün grafikler (.png) ve tablolar (.csv) |

## Özet

- **Soru 1:** Arıza oranı %3,4 (ciddi sınıf dengesizliği). En yararlı değişkenler tork, dönüş hızı ve takım aşınması; güç (tork × devir) ve sıcaklık farkı arızanın fiziksel nedenini ölçüyor.
- **Soru 2:** Lojistik Regresyon, KNN ve Karar Ağacı; stratified %80/%20 bölme, 5 katlı K-Fold ile ayar ve eşik seçimi, fiziğe dayalı yeni özellikler (güç, sıcaklık farkı, zorlanma oranı). Test F1 (ham → geliştirilmiş): LR 0,198 → 0,593 · KNN 0,487 → 0,578 · **Karar Ağacı 0,769 → 0,876** (yanlış alarm 0). Seçilen model: geliştirilmiş Karar Ağacı (en düşük maliyet, 9 kurallık açıklanabilir yapı, hızlı, zaman sıralı testte de dayanıklı).
- **Soru 3:** Kaçan arıza (yanlış negatif) daha kritik. Yakalamayı artırma yolları (eşik, yeni özellikler, sınıf ağırlığı) ve olumsuz yanları; aşırı öğrenme ölçümü ve iki somut öneri.

TWF, HDF, PWF, OSF, RNF, UDI ve Product ID sınav şartı gereği model girdisi olarak kullanılmadı.

## Çalıştırma

```bash
cd kod
pip install -r requirements.txt
jupyter nbconvert --to notebook --execute --inplace sinav_cozumu.ipynb
```

Sonuçlar `random_state=42` ile her çalıştırmada aynıdır.
