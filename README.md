
# Hayvan Sınıflandırma Projesi

kaggle proje linki: 

  Bu proje, **Convolutional Neural Network (CNN)** kullanarak 10 farklı hayvan sınıfını sınıflandırmak amacıyla geliştirilmiştir. Proje, veri hazırlama, model eğitimi, test setleri üzerinde değerlendirme ve farklı manipülasyon tekniklerinin etkilerini analiz etme aşamalarını içermektedir.

## **Proje Adımları**

### **1. Veri Hazırlama**
- Kaggle'dan indirilen [Animals with Attributes 2](https://www.kaggle.com/datasets/rrebirrth/animals-with-attributes-2) veri seti kullanıldı.
- Sadece şu 10 hayvan sınıfı seçildi: 
  - `collie`, `dolphin`, `elephant`, `fox`, `moose`, `rabbit`, `sheep`, `squirrel`, `giant panda`, `polar bear`.
- Her sınıftan 650 resim seçildi.
- Resimler, CNN modeline uygun boyutlara (128x128 piksel) yeniden boyutlandırıldı ve normalize edildi.

### **2. Veri Artırma**
- Eğitim setindeki veriler için veri artırma (data augmentation) teknikleri uygulandı:
  - Parlaklık ve kontrast değişimi
  - Döndürme (rotation)
  - Gürültü ekleme (noise)
  - Yansıtma (flip)

### **3. CNN Modeli Tasarımı**
- **Convolutional Neural Network (CNN)** modeli aşağıdaki katmanlardan oluşmaktadır:
  - 3 adet konvolüsyon katmanı (Conv2D) ve maksimum havuzlama (MaxPooling2D)
  - Fully connected (yoğun) katmanlar
  - Dropout katmanları ile aşırı öğrenmeyi önleme
- Aktivasyon fonksiyonu olarak **ReLU** kullanılmıştır.
- Çıkış katmanında 10 sınıf için **softmax** aktivasyon fonksiyonu yer almaktadır.
- Kayıp fonksiyonu olarak **categorical_crossentropy**, optimizasyon için **Adam** algoritması kullanılmıştır.

### **4. Test Setleri ile Değerlendirme**
#### a. Orijinal Test Seti
- Eğitim sırasında modelin genelleme performansı ölçüldü.

#### b. Manipüle Edilmiş Test Seti
- Test setine parlaklık, kontrast ve renk manipülasyonları uygulandı.
- Manipüle edilmiş test seti ile modelin performansı değerlendirildi.

#### c. Renk Sabitliği Uygulanan Test Seti
- Manipüle edilmiş test setine **Gray World Algoritması** kullanılarak renk sabitliği uygulandı.
- Bu veri setiyle modelin performansı tekrar test edildi.

### **5. Performans Karşılaştırması**
- Üç farklı test setindeki başarı oranları karşılaştırıldı ve raporlandı:
  - **Orijinal Test Seti**
  - **Manipüle Edilmiş Test Seti**
  - **Renk Sabitliği Uygulanan Test Seti**

## **Kullanılan Teknolojiler**
- **Python**: Programlama dili
- **TensorFlow/Keras**: Derin öğrenme modeli geliştirme
- **OpenCV**: Görüntü işleme
- **Albumentations**: Veri artırma işlemleri
- **Matplotlib**: Görselleştirme

## **Sonuçlar**
Bu projede:
1. CNN modeli, orijinal test setinde %58.7 doğruluk oranıyla temel bir başarı göstermiştir.
2. Manipüle edilmiş test setinde, modelin performansı %52.1’e düşmüştür. Bu, farklı ışık koşullarının modelin genelleme yeteneğini etkilediğini göstermektedir.
3. Renk sabitliği uygulanmış test setinde doğruluk oranı %43.4’e düşmüştür. Bu durum, renk sabitliği algoritmasının bu veri seti ve model için uygun olmadığını göstermektedir.
