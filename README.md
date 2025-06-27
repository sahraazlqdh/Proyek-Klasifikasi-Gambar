# Proyek Klasifikasi Bahasa Isyarat 🧏🏻‍♂️🧏🏻‍♀️🤟🏼✋🏼👐🏼

Proyek ini bertujuan untuk membangun model klasifikasi gambar menggunakan dataset **Sign Language MNIST** dari Kaggle. Model dikembangkan menggunakan CNN (Convolutional Neural Network) berarsitektur *Sequential*, dan diekspor dalam tiga format: **SavedModel**, **TensorFlow Lite (TFLite)**, dan **TensorFlow.js (TFJS)**.

## 🔍 Deskripsi Dataset
- Dataset: [Sign Language MNIST – Kaggle](https://www.kaggle.com/datasets/datamunge/sign-language-mnist)
- Format: CSV (28x28 grayscale pixels per gambar)
- Jumlah total gambar: **27.455**
  - Train: 27.455 gambar
  - Test: 7.172 gambar
- Jumlah kelas: **24** huruf alfabet (A–Y, tanpa J dan Z)

## ⚙️ Pembagian Dataset
Dataset CSV dibagi ulang dengan `train_test_split` untuk membuat validasi:
- **Train Set:** 80% (24.238 gambar)
- **Validation Set:** 10% (5.194 gambar)
- **Test Set:** 10% (5.195 gambar)

## 🧠 Arsitektur Model
Model CNN dibangun dari nol menggunakan `tf.keras.Sequential`:
- **Conv2D** → **ReLU** → **MaxPooling2D**
- **Conv2D** → **ReLU** → **MaxPooling2D**
- **Flatten** → **Dense(128)** → **Dropout(0.3)** → **Dense(num_classes, softmax)**

## 📈 Hasil Model
| Data        | Akurasi     |
|-------------|-------------|
| Train       | **88.7%**  |
| Validation  | **99.25%**  |
| Test        | **99.15%**  |

## 📊 Visualisasi Training
Notebook menyajikan plot akurasi dan loss selama 30 epoch training, sehingga memudahkan evaluasi performa dan overfitting.

## 📤 Ekspor Model
Model telah diekspor dalam 3 format standar produksi:
1. **SavedModel** – Untuk keperluan server-side atau TF Serving
2. **TFLite** – Untuk deployment mobile (Android/iOS)
3. **TensorFlow.js** – Untuk deployment di browser/web

## 🧪 Inference TFLite
Notebook juga menampilkan proses *inference* dari model TFLite terhadap 10 gambar test secara acak, beserta perbandingan label asli dan prediksi.

Berikut outputnya:
Sampel 1: Prediksi = 6, Asli = 6
Sampel 2: Prediksi = 5, Asli = 5
Sampel 3: Prediksi = 10, Asli = 10
Sampel 4: Prediksi = 0, Asli = 0
Sampel 5: Prediksi = 3, Asli = 3
Sampel 6: Prediksi = 21, Asli = 21
Sampel 7: Prediksi = 10, Asli = 10
Sampel 8: Prediksi = 14, Asli = 14
Sampel 9: Prediksi = 3, Asli = 3
Sampel 10: Prediksi = 7, Asli = 7

📌 Akurasi inference dari 10 sampel: 100% benar.
Hal ini menunjukkan bahwa model TFLite mampu melakukan prediksi dengan presisi tinggi, dan konversi model tidak mengurangi performanya secara signifikan.
