1- Görüntü Nedir?
——————————————————————————————————————-
Bir resmi bilgisayar sayılar halinde oluşan matrislerden oluşur.
Siyah-Beyaz bir resimde her kare 0-255 arasında değer alır

0-> siyah
255 -> beyaz
Değerlerini alır

Renkli Resimlerde 3 kanala vardır
Kırmızı (R), Yeşil(G), Mavi (B)
Yani bir resim 3 ayrı matrisin üst üste konmuş hali gibidir

Bir resmi projelerde gri tonlarına çevirme sebebimiz daha basit şekilde karşılaştırma yapmaktır
Daha basit = tek kanal sadece parlıklık kalır
Daha hızlı = hesaplamalarda tek kanal karşılaştırılır
Algoritmalar = gri tonlarda daha iyi çalışır


Matematiksel olarak gri değer hesaplama 


Gray= 0.299*R + 0.587*G+ 0.114*B


***İnsan gözü yeşile daha duyarlıdır

2- Resim arasındaki benzerlik nasıl çözülür
——————————————————————————————————————————

En basit yöntem=


MSE = (1 / N) Σ (X - Y)²

Ama bu yöntem yeterli karşılaştırmayı sağlamaz bunun için SSIM kullanırız

SSIM NEDİR?

SSIM 3 şeye bakar:

1-parlaklık benzerliği
	Ortalama parlaklıklar (µ) karşılaştırılır.

2-Kontrast benzerliği 
	Varyans (σ²) değerleri karşılaştırılır.

3-Yapısal benzerlik 
	Kovaryans (σxy) ile iki resimdeki desenler/şekiller benzer mi bakılır.










SSIM sonuçları 0-1 arasında benzerlik oranı yapar.

Kodlarken izlediğimiz yol şudur:

Resimleri griye çevir
Her piksel çevresindeki küçük pencerede ortalama varyansı hesapla
SSIM formülü uygula
Bütün resim için ortalama SSIM değeri alınır


Örnek hesaplama :

X = [[100, 120],
     [130, 140]]

Y = [[102, 118],
     [128, 142]] 
 

Elimizde 2 matris var 
	•	Ortalama µx ≈ 122.5
	•	Ortalama µy ≈ 122.5

SSIM değeri = 0.99 çıkar çok benzer


