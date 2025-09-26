# Akbank-Derin-Ogrenme-Bootcamp
Akbank Derin Ogrenme Bootcamp 26.09.2025 Tarihli proje teslim dosyasıdır. 

# Giriş 

  Bu proje, Intel Görüntü Sınıflandırması veri setini kullanarak altı farklı ortamı güvenilir bir şekilde ayırt etme yeteneğine sahip bir CNN Mimarisi geliştirmeye odaklanmıştır. TensorFlow/Keras altyapısıyla hayata geçirilen modelde, ilk aşamada veri setinin genelleme yeteneğini artırmak amacıyla kapsamlı Data Augmentation teknikleri uygulanmıştır. Modelin çekirdek yapısı, öznitelik çıkarımı için Conv2D ve MaxPooling2D, öğrenme kararlılığı için BatchNormalization katmanlarından oluşmuş; tam bağlantılı katmanlarda ise Dropout mekanizması (Dropout(0.4) ve Dropout(0.2)) kullanılarak Overfitting riski başlangıçtan itibaren kontrol altında tutulmaya çalışılmıştır. Tüm analiz ve görselleştirme adımlarında NumPy, Matplotlib, scikit-learn ve OpenCV kütüphanelerinden faydalanılmıştır.

# Metrikler

  Geliştirilen model, zorlu test seti üzerinde genel bir başarı göstererek %84 Doğruluk (Accuracy) ve %84 F1-Score oranına ulaşmıştır. Kayıp ve Başarı Eğrileri incelendiğinde, modelin 6. epoch'tan sonra Doğrulama Kaybı'nda (Val_Loss) dalgalanma ve yükselme eğilimine girdiği gözlemlenmiştir; bu durum, modelin hafif bir Overfitting eğilimi taşıdığını göstermiştir. Classification Report sonuçları ise, modelin Forest (F1: 0.95) ve Street (F1: 0.86) gibi sınıflarda çok güçlü olduğunu, ancak Glacier (F1: 0.78) ve Mountain (F1: 0.79) sınıflarını ayırt etmede zorlandığını, dolayısıyla bu iki sınıfın performansının genel ortalamanın altında kaldığını netleştirmiştir

# Ekler

  Projenin teknik çözümler açısından en önemli bölümü, modelin karar mekanizmasını şeffaflaştıran Grad-CAM (Heatmap Görselleştirme) analizidir.
  Bu projenin görselleştirme çalışması, Grad-CAM (Gradient-weighted Class Activation Mapping) tekniği ile gerçekleştirilmiştir. Grad-CAM, bir nevi modelin dikkat haritasını çıkararak, tahmin yaparken görüntünün hangi piksel bölgelerine odaklandığını ısı haritası (heatmap) şeklinde gösterir. Bu çalışma, projenin sadece sayısal metriklerle sınırlı kalmayıp, görsel doğrulama içerdiğini kanıtlamaktadır:Üretilen heatmap'ler, modelin tahmin yaparken görüntünün en kritik bölgelerine (yapısal sınıflarda hatlar, doğal sınıflarda dokular) odaklandığını kanıtlayarak, kararlarının mantıksal temelini doğrulamıştır.

# Sonuç ve Gelecek Çalışmalar

  Modelin %84 başarıya ulaşması temel hedefi karşılasa da, sonuçlar gelecekteki çalışmalar için net iyileştirme alanları sunmaktadır. Overfitting eğilimini kontrol altına almak için, eğitimin 6. epoch civarında otomatik durmasını sağlayacak Erken Durdurma (Early Stopping) mekanizmasının eklenmesi birinci önceliktir. İkinci olarak, Glacier ve Mountain sınıflarının performansını artırmak amacıyla, bu sınıflar arasındaki zorlu ayrımları daha iyi yakalayabilecek daha derin Conv katmanları veya daha fazla filtre eklenmesi hedeflenmelidir. Ayrıca, modelin genelleme yeteneğinin sınırlarını zorlamak adına Transfer Öğrenme yaklaşımları denenmelidir.
