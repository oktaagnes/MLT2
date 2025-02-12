# Laporan Proyek Machine Learning - Okta Agnes Ladyagatha Manik

## Project Overview

Di era digital saat ini, ketersediaan film di berbagai platform streaming semakin melimpah. Akibatnya, pengguna sering kali menghadapi kesulitan dalam menemukan film yang sesuai dengan preferensi mereka. Untuk mengatasi tantangan ini, sistem rekomendasi film hadir sebagai solusi utama, membantu pengguna menavigasi beragam pilihan dan menemukan film yang paling relevan dengan minat mereka. Dengan menerapkan algoritma yang canggih, sistem rekomendasi tidak hanya meningkatkan pengalaman pengguna tetapi juga berkontribusi pada retensi dan kepuasan pelanggan.

Pengembangan sistem rekomendasi film ini penting karena beberapa alasan:

1. **Personalisasi Pengalaman Pengguna**: Dengan menyediakan rekomendasi yang akurat dan sesuai dengan preferensi individu, pengguna dapat dengan mudah menemukan film yang mereka minati tanpa perlu menghabiskan waktu yang lama untuk mencari.
2. **Meningkatkan Engagement**: Sistem rekomendasi yang efektif mampu meningkatkan keterlibatan pengguna dalam platform, yang pada akhirnya berkontribusi terhadap peningkatan loyalitas pelanggan.
3. **Keunggulan Kompetitif**: Bagi penyedia layanan streaming, sistem rekomendasi yang unggul dapat menjadi faktor pembeda yang meningkatkan daya saing mereka di industri hiburan digital.

### Hasil Riset dan Referensi

Beberapa penelitian telah menunjukkan efektivitas algoritma Content-Based Filtering dan Collaborative Filtering dalam sistem rekomendasi. Artikel oleh **Ahmad Shlihin. (2022)** memperkenalkan Collaborative Filtering sebagai metode yang efektif dalam merekomendasikan item berdasarkan interaksi pengguna. Sementara itu, **Pazzani dan Billsus (2007)** menjelaskan bagaimana Content-Based Filtering dapat memanfaatkan atribut konten untuk memberikan rekomendasi yang lebih personal. Dataset MovieLens 100K, yang sering digunakan dalam penelitian ini, menyediakan data interaksi pengguna dengan film yang kaya dan memungkinkan pengembangan serta evaluasi model rekomendasi yang handal.

## Referensi

1. MovieLens Dataset. (n.d.). Retrieved from [https://grouplens.org/datasets/movielens/100k/]
2. Pazzani, M., & Billsus, D. (2007). Content-based recommendation systems. In _The adaptive web_ (pp. 325-341). Springer, Berlin, Heidelberg. [https://link.springer.com/chapter/10.1007/978-3-540-72079-9_10]
3. Ahmad Sholihin (2022). Rekomendasi menggunakan Content Based Filtering dan Collaborative Filtering [https://medium.com/@ahmadsholihin1705/rekomendasi-menggunakan-content-based-filtering-dan-collaborative-filtering-2aab2aec8ebe]

## Business Understanding

Dalam pengembangan sistem rekomendasi film, penting untuk memahami tantangan utama yang dihadapi pengguna dan platform. Beberapa masalah yang diidentifikasi adalah:

1. **Overwhelming Choice**: Pengguna sering merasa kewalahan dengan banyaknya pilihan film, sehingga sulit untuk menemukan yang paling sesuai.
2. **Cold Start Problem**: Pengguna baru atau film baru seringkali tidak memiliki cukup data interaksi untuk memberikan rekomendasi yang akurat.
3. **Sparsity of Data**: Banyak pengguna yang hanya memberikan sedikit rating atau interaksi, membuat model rekomendasi menjadi kurang efektif.

### Problem Statements

1. Bagaimana cara mengembangkan sistem rekomendasi film yang dapat memberikan rekomendasi yang akurat dan relevan kepada pengguna berdasarkan preferensi mereka?
2. Bagaimana mengatasi masalah cold start dan sparsity dalam dataset MovieLens 100K untuk meningkatkan performa sistem rekomendasi?

### Goals

1. Membangun model sistem rekomendasi film menggunakan 2 algoritma yang berbeda yaitu Content-Based Filtering dan Collaborative Filtering untuk mendapatkan rekomendasi film yang beragam.
2. Mengoptimalkan algoritma Cosine Similarity dan Singular Value Decomposition (SVD) dalam konteks dataset MovieLens 100K untuk mengatasi masalah sparsity dan cold start.

Semua poin di atas harus diuraikan dengan jelas. Anda bebas menuliskan berapa pernyataan masalah dan juga goals yang diinginkan.

#### 1. Content-Based Filtering (CBF) dengan Cosine Similarity

**Pendekatan Content-Based Filtering (CBF) berfokus pada analisis atribut konten dari film, seperti genre, aktor, sutradara, serta deskripsi film, untuk memberikan rekomendasi yang sesuai dengan preferensi pengguna.**

- **Tahap Proses**:
  - **Ekstraksi Fitur**: Mengidentifikasi dan mengekstraksi fitur-fitur utama dari setiap film dalam dataset MovieLens 100K.
  - **Representasi Vektor**: Mengonversi fitur-fitur tersebut ke dalam bentuk representasi vektor numerik untuk mempermudah analisis.
  - **Perhitungan Similarity**: Menggunakan metode Cosine Similarity untuk menghitung tingkat kemiripan antara film berdasarkan representasi vektornya.
  - **Rekomendasi**: Menampilkan film dengan tingkat kemiripan tertinggi terhadap film yang telah dinilai atau disukai oleh pengguna.

#### 2. Collaborative Filtering (CF) dengan Singular Value Decomposition (SVD)

**Pendekatan Collaborative Filtering (CF) memanfaatkan data interaksi pengguna dengan film untuk mengidentifikasi pola serta hubungan tersembunyi antara pengguna dan item yang direkomendasikan.**

- **Proses**:
  - **Matrix Factorization**: Menerapkan teknik Singular Value Decomposition (SVD) untuk mendekomposisi matriks interaksi pengguna-film menjadi tiga matriks lebih kecil (U, Σ, dan V^T) yang merepresentasikan fitur pengguna serta fitur film.
  - **Prediksi Rating**: Melakukan perkalian kembali matriks-matriks hasil dekomposisi untuk memprediksi rating yang belum diberikan oleh pengguna terhadap film tertentu..
  - **Penyajian Rekomendasi**: Menyajikan film yang sesuai dengan preferensi pengguna

Dengan menggabungkan kedua pendekatan ini, diharapkan sistem rekomendasi yang dibangun dapat memanfaatkan keunggulan masing-masing metode, memberikan rekomendasi yang lebih akurat dan relevan kepada pengguna, serta mengatasi tantangan seperti cold start dan sparsity dalam dataset.

## Data Understanding

Dataset yang digunakan dalam proyek ini adalah MovieLens100K, yang berisi 100.000 penilaian dari pengguna untuk berbagai film, dataset ini terdiri dari 4 komponen data yang berbeda
Dataset diambil dari [https://grouplens.org/datasets/movielens/100k/]

**Links Dataset**
**Pada data links dataset terdapat 9742 baris dan 3 kolom yang dimana terdapat 8 baris yang memiliki null untuk kolom tmbdId dan tidak terdapat baris yang duplikat**

- movieId : merupakan kolom yang berisi unique id dari setiap movie(film) dan terdapat 9742 unique movie(film)
- imdbId : merupakan kolom yang merujuk pada id sebuah film di website imdb
- tmbdId : merupakan kolom yang merujuk pada id sebuah film di website tmdb
- **Movies Dataset**
  **Pada data movies dataset terdapat 9742 baris dan 3 kolom dan tidak terdapat baris yang memiliki null maupun baris yang duplikat**
  - movieId : merupakan kolom yang berisi unique id dari setiap movie(film) dan terdapat 9742 unique movie(film)
  - title : merupakan kolom yang berisi judul(nama film)
  - genre : merupakan kolom yang berisi genre dari setiap film, untuk genrenya bisa terdapat lebih dari 1 genre untuk setiap film, dan terdapat 19 unique genre
- **Ratings Dataset**
  **Pada data links dataset terdapat 100836 baris dan 4 kolom dan tidak terdapat baris yang memiliki null maupun baris yang duplikat**
  - userId : merupakan kolom yang berisi unique id dari setiap user yang memberi rating terhadap film yang ditonton dan terdapat 610 unique user
  - movieId : merupakan kolom yang berisi unique id dari setiap film yang telah ditonton oleh seorang user
  - rating : merupakan kolom yang berisi rating film yang diberikan oleh user
  - timestamp : merupakan kolom yang berisi waktu dan tanggal user memberikan rating
- **Tags Dataset**
  **Pada data links dataset terdapat 3683 baris dan 4 kolom dan tidak terdapat baris yang memiliki null maupun baris yang duplikat**
  - userId : merupakan kolom yang berisi unique id dari setiap user yang memberi tag terhadap film yang ditonton
  - movieId : merupakan kolom yang berisi unique id dari setiap film yang telah ditonton oleh seorang user
  - tag : merupakan kolom yang berisi tag dari film yang telah ditonton oleh seorang user
  - timestamp : merupakan kolom yang berisi waktu dan tanggal user memberikan rating

## Data Preparation

Pada tahap data preparation saya melakukan transformasi berupa pembersihan judul film yang masih mengandung tahun rilis film, melakukan pembuatan kolom baru bernama features dengan cara menggabungkan judul film dan genre.

### General Data Preparation

- Tahapan ini membersihkan kolom genres dengan menghapus karakter khusus seperti [] dan tanda |
  - Alasan: Membersihkan data ini penting untuk memastikan bahwa informasi genre dapat diproses secara konsisten saat digunakan dalam model. Tanpa preprocessing ini, teks yang ada di kolom genres mungkin sulit untuk diekstrak dan dianalisis dengan benar oleh TfidfVectorizer.

### Data Preparation untuk Modelling Content Based Filtering

- Membuat kolom baru features yang menggabungkan informasi dari kolom title dan genres. Dengan cara ini, informasi judul dan genre dari film diubah menjadi satu representasi teks.

  - Alasan: Tahap ini penting karena memungkinkan model untuk mempertimbangkan kesamaan film berdasarkan judul dan genre, yang meningkatkan akurasi dalam rekomendasi berbasis konten. Kombinasi fitur ini memberikan konteks yang lebih luas tentang film dibandingkan jika hanya menggunakan genre saja.

- Melakukan transformasi menggunakan TF-IDF Vectorization
  - Alasan: Kolom features dikonversi menjadi representasi numerik menggunakan TF-IDF (_Term Frequency-Inverse Document Frequency_), yang memberikan bobot lebih besar pada kata-kata unik dan membedakan film satu dengan lainnya.

### Data Preparation untuk Modelling Collaborative Filtering

- Menggunakan data ratings dengan menggunakan kolom usersId, movieId, ratings

  - Alasan: Menggunakan kolom userId, movieId, dan ratings diperlukan karena format ini memungkinkan pemodelan preferensi pengguna secara eksplisit. Collaborative filtering memanfaatkan interaksi historis (rating) untuk menemukan pola kesamaan antar pengguna atau item, membantu dalam memberikan rekomendasi yang lebih akurat.

- Membagi data menjadi Train dan Testing menggunakan surprise model selection
  - Alasan: Pemrosesan ini diperlukan untuk memastikan model dilatih dengan baik, lalu diuji guna memastikan bahwa model dapat merekomendasikan film dengan akurasi yang dapat diandalkan.

## Modeling

Pada tahap modelling saya menggunakan 2 model algoritma yang berbeda yaitu Content Based Filtering (Cosine Similarity) dan Collaborative Filtering (Singular Value Decomposition)

### Content Based Filtering

Pada metode _content-based filtering_, model melakukan rekomendasi berdasarkan kesamaan konten film (judul dan genre) dibandingkan dengan film yang diberikan oleh pengguna.

#### Cara Kerja dan Parameter

Langkah-langkah pada _content-based filtering_:

- **Cosine Similarity**: Untuk menghitung kesamaan antarfilm, digunakan _cosine similarity_, yang mengukur sudut antarvektor dalam ruang multidimensi. Hasil nilai _cosine similarity_ berkisar antara 0 hingga 1, dengan nilai 1 menandakan film sangat mirip dan 0 menandakan tidak ada kesamaan.

#### Alur Kerja Fungsi `recommend_movies`

1. **Input Film**: Pengguna memberikan judul film (misalnya "Inception") sebagai input.
2. **Pencarian Indeks**: Sistem mencari indeks film berdasarkan judul input di dataframe `movies`.
3. **Perhitungan Similarity**: Cosine similarity digunakan untuk mengukur kesamaan antara film input dan seluruh film dalam dataset. Cosine similarity menghitung kemiripan dua vektor dengan membandingkan sudut di antara keduanya, di mana nilai 1 berarti sangat mirip dan 0 berarti tidak mirip.
4. **Penyortiran Skor Kesamaan**: Semua film diurutkan berdasarkan skor kesamaan dengan film input, dari yang paling mirip hingga yang paling rendah.
5. **Pemilihan Top-10 Rekomendasi**: Sistem mengabaikan film input dan memilih 10 film paling mirip berdasarkan skor tertinggi.
6. **Output**: Mengembalikan judul, ID, dan genre dari 10 film teratas sebagai rekomendasi.

#### Rekomendasi

Setelah menghitung kesamaan antarfilm, saya mengurutkan film berdasarkan skor kesamaan tertinggi dan merekomendasikan 10 film teratas yang paling mirip dengan film input. Berikut adalah contoh hasil rekomendasi berbasis _content-based filtering_ untuk film **"Heat"**:
![alt text](https://github.com/oktaagnes/MLT2/blob/main/heat.png?raw=true)
gambar 1 rekomendasi

### Collaborative Filtering

Model _collaborative filtering_ dalam proyek ini dilatih menggunakan data rating pengguna terhadap film. Model mempelajari pola preferensi dengan menguraikan matriks rating menjadi beberapa faktor laten (fitur yang tidak terlihat secara langsung) yang merepresentasikan hubungan antara pengguna dan film.

#### Cara Kerja dan Parameter yang Digunakan

Langkah-langkah dalam membangun dan mengevaluasi model ini adalah sebagai berikut:

#### Alur Kerja Sistem Rekomendasi

1. **Pemodelan dengan SVD**:

   - SVD adalah teknik dekomposisi matriks yang memecah matriks besar (user-item ratings) menjadi representasi lebih kecil, menangkap hubungan laten antara pengguna dan item.
   - Setelah model dilatih pada data training, SVD menghasilkan faktor-faktor laten yang menggambarkan preferensi pengguna dan karakteristik film.

2. **Prediksi Rating**:

   - Setelah pelatihan, model digunakan untuk memprediksi rating yang mungkin diberikan oleh pengguna pada film yang belum mereka tonton.

3. **Fungsi `get_recommendations`**:

   - Fungsi ini menerima **user_id** dan dataframe film sebagai input.
   - Pertama, sistem mengidentifikasi film yang sudah dirating oleh pengguna dan memisahkan film yang belum pernah ditonton (unrated).
   - Untuk setiap film yang belum dirating, sistem membuat prediksi menggunakan metode `model.predict()`.
   - Prediksi ini diurutkan dari yang tertinggi ke terendah, dan 10 film teratas dipilih sebagai rekomendasi.

4. **Output**:
   - Fungsi mengembalikan judul dan genre dari 10 film terbaik sebagai rekomendasi untuk pengguna tersebut.

### Teknologi yang Digunakan

- **SVD (Singular Value Decomposition)**:  
  SVD digunakan untuk memetakan pengguna dan film ke dalam ruang laten, memprediksi rating bahkan ketika sebagian besar data rating tidak tersedia (sparse matrix). Algoritma ini sangat efektif untuk rekomendasi karena dapat menangkap pola-pola tersembunyi dalam data interaksi pengguna dan film.

Pendekatan **Collaborative Filtering dengan SVD** ini unggul karena tidak memerlukan fitur eksplisit dari item (film), melainkan hanya berdasarkan pola interaksi pengguna. Dengan demikian, sistem dapat merekomendasikan film yang relevan meskipun pengguna dan item baru tidak memiliki deskripsi atau fitur yang lengkap.

### 4. Rekomendasi Top N Film

Sebagai contoh, berikut adalah rekomendasi untuk pengguna dengan **title heat** berdasarkan prediksi rating tertinggi yang dihasilkan oleh model SVD:
gambar heat

### Kelebihan dan Kekurangan

#### Content Based Filtering

- **Keunggulan**
  - **Deskripsi Pendekatan**: Pendekatan Content-Based Filtering (CBF) menganalisis karakteristik film, seperti genre, aktor, sutradara, dan deskripsi, untuk menemukan film yang memiliki kesamaan dengan yang telah ditonton atau disukai oleh pengguna. Algoritma Cosine Similarity digunakan untuk mengukur tingkat kemiripan antarfilm berdasarkan representasi vektor fitur masing-masing.
  - **Implementasi**: Setiap film direpresentasikan dalam bentuk vektor fitur yang mencerminkan atribut film. Cosine Similarity kemudian digunakan untuk menghitung kesamaan antara vektor film yang telah diberi rating tinggi oleh pengguna dengan vektor film lainnya. Berdasarkan hasil perhitungan ini, sistem akan merekomendasikan film yang memiliki tingkat kemiripan tertinggi.
  - **Kelebihan**: Rekomendasi yang Lebih Personal. Sistem mampu memberikan rekomendasi yang spesifik berdasarkan karakteristik film yang telah disukai oleh pengguna.Cocok untuk Pengguna Baru. Content-Based Filtering dapat berfungsi dengan baik bagi pengguna baru yang belum memiliki riwayat rating karena sistem hanya bergantung pada atribut film, bukan data interaksi pengguna lainnya..
- **Kekurangan**
  - **Terbatas pada Konten yang Serupa**: Sistem hanya dapat merekomendasikan film yang memiliki karakteristik serupa dengan film yang telah dinikmati sebelumnya, sehingga rekomendasi yang dihasilkan cenderung kurang beragam.
  - **Masalah Cold Start untuk Item Baru**: Jika terdapat film baru dengan sedikit atau tanpa metadata, sistem akan kesulitan memberikan rekomendasi yang akurat.
  - **Keterbatasan pada Preferensi Pengguna**: Sistem tidak mampu merekomendasikan film di luar pola preferensi pengguna yang sudah ada, sehingga pengguna mungkin tidak mendapatkan rekomendasi film dari genre atau kategori yang belum pernah mereka eksplorasi sebelumnya.

#### Collaborative Filtering (Singular Value Decomposition - SVD)

- **Keunggulan**:

  - **Mampu Mengungkap Pola Kompleks**:SVD dapat menangkap hubungan laten antara pengguna dan film yang tidak dapat diidentifikasi melalui pendekatan berbasis konten, sehingga menghasilkan rekomendasi yang lebih bervariasi dan akurat.
  - **Pengurangan Dimensionalitas**: Dengan melakukan dekomposisi matriks, SVD dapat mengurangi jumlah dimensi dalam data, yang berkontribusi pada peningkatan efisiensi komputasi serta mengurangi noise dalam data.

- **Kekurangan**

  - **Masalah Cold Start untuk Pengguna Baru**: Pendekatan ini bergantung pada data interaksi pengguna, sehingga pengguna baru yang belum memberikan penilaian pada film akan mengalami kesulitan dalam memperoleh rekomendasi yang relevan.
  - **Permasalahan Sparsity**: Pada dataset berskala besar, biasanya hanya sebagian kecil pengguna yang memberikan penilaian terhadap sebagian kecil film, menghasilkan matriks interaksi yang jarang (sparse). Hal ini dapat menurunkan efektivitas algoritma dalam memberikan rekomendasi yang optimal.
  - **Kompleksitas Komputasi yang Tinggi**: Proses dekomposisi matriks dalam SVD memiliki tingkat kompleksitas yang tinggi, terutama ketika diterapkan pada dataset berukuran besar. Hal ini dapat meningkatkan kebutuhan akan sumber daya komputasi yang signifikan.

  Pendekatan Content-Based Filtering (CBF) dan Collaborative Filtering (CF) dengan SVD memiliki keunggulan dan keterbatasan masing-masing. Oleh karena itu, mengombinasikan kedua metode ini dapat menjadi strategi yang efektif untuk meningkatkan kualitas rekomendasi dengan menutupi kelemahan yang terdapat pada masing-masing pendekatan.

## Evaluation

### Langkah-Langkah

1. **Preprocessing Data**: Data film diolah dengan menggabungkan kolom `title` dan `genres` menjadi satu kolom `features` untuk mendapatkan representasi konten.
2. **Vectorization**: Kolom `features` diubah menjadi representasi vektor menggunakan TF-IDF (Term Frequency-Inverse Document Frequency).
3. **Cosine Similarity**: Dihitung kesamaan antarfilm dengan Cosine Similarity berdasarkan vektor TF-IDF. Nilai Cosine Similarity yang lebih tinggi menunjukkan tingkat kemiripan konten yang lebih besar.
4. **Evaluasi Model**: Model dievaluasi menggunakan metrik **Precision@K**, **Recall@K**, **Mean Average Precision (MAP)**, dan **Mean Reciprocal Rank (MRR)** untuk mengukur kinerja rekomendasi.

### Content Based Filtering

### Metrik Evaluasi yang Digunakan

Berikut adalah metrik evaluasi yang digunakan untuk mengukur kinerja sistem rekomendasi:

1. _Precision@K_
2. _Recall@K_

#### 1. Precision@K

Precision@K mengukur proporsi rekomendasi yang relevan di antara K rekomendasi teratas yang diberikan oleh sistem. Precision tinggi menunjukkan bahwa sistem mampu memberikan rekomendasi yang relevan untuk pengguna.

- _Formula Precision@K_:
  (Jumlah item yang relevan dalam top K) / K</span>

- _Cara Kerja Precision@K_:
  Precision@K bekerja dengan menghitung berapa banyak film yang relevan di antara K film yang direkomendasikan pertama. Jika K diatur ke 10, maka Precision@10 akan menunjukkan persentase film relevan dari 10 rekomendasi teratas.

#### 2. Recall@K

Recall@K mengukur proporsi item relevan yang direkomendasikan oleh sistem dari seluruh item relevan yang tersedia. Metrik ini membantu memastikan bahwa sistem tidak melewatkan item yang relevan.

- _Formula Recall@K_:
  (Jumlah item yang relevan dalam top K) / (Jumlah total item relevan)

- _Cara Kerja Recall@K_:
  Recall@K menghitung persentase item relevan yang direkomendasikan dari seluruh item relevan untuk setiap judul. Misalnya, jika ada 20 film yang relevan untuk "Heat" dan sistem merekomendasikan 10 di antaranya di posisi teratas, maka Recall@10 akan menunjukkan seberapa banyak item relevan yang ditemukan dari seluruh item relevan.

### Hasil Evaluasi Proyek Berdasarkan Metrik

Evaluasi sistem rekomendasi ini dilakukan pada beberapa judul film dengan ground truth yang telah ditentukan. Berikut hasil evaluasinya dengan menggunakan nilai \( K = 10 \) pada metrik di atas:

- _Precision@10_: Metrik ini menunjukkan berapa banyak film relevan yang berhasil direkomendasikan di antara 10 rekomendasi teratas. Precision yang tinggi menunjukkan bahwa rekomendasi yang diberikan cukup relevan dengan input pengguna.

- _Recall@10_: Metrik ini menunjukkan seberapa banyak item relevan yang berhasil ditemukan dari seluruh item relevan yang tersedia. Recall yang tinggi menunjukkan bahwa sistem mampu menemukan sebagian besar film relevan untuk setiap judul.

### 3. Hasil Evaluasi

Berdasarkan hasil evaluasi, berikut adalah performa sistem rekomendasi pada dua film input, _"Heat"_ dan _"Jumanji"_:

- **Heat**:

  - Precision@5: 81.97%
  - Recall@5: 72.21%

  Untuk film _Heat_, _precision_ sebesar 74.06% menunjukkan bahwa sebagian besar dari 5 rekomendasi teratas memiliki kesamaan yang cukup kuat dengan film input. _Recall_ sebesar 71.55% menunjukkan bahwa dari seluruh rekomendasi yang relevan, model telah berhasil menangkap sekitar 71% film mirip dalam rekomendasi teratas.

- **Jumanji**:

  - Precision@5: 12.85%
  - Recall@5: 100.00%

  Untuk _Jumanji_, hasil _precision_ yang rendah sebesar 12.85% menunjukkan bahwa model tidak memberikan rekomendasi yang secara ketat relevan di antara _top 5_. Namun, nilai _recall_ 100% menunjukkan bahwa meskipun ketepatan rekomendasi di antara _top 5_ kurang, model berhasil menangkap seluruh film yang relevan yang mungkin mirip dengan _Jumanji_ dalam _cosine similarity_.

Metrik evaluasi _precision_ dan _recall_ digunakan untuk memastikan bahwa sistem rekomendasi memiliki relevansi dan cakupan yang baik, sesuai dengan kebutuhan pengguna. Dalam proyek ini, hasil menunjukkan bahwa untuk film tertentu seperti _Toy Story_, sistem berhasil memberikan rekomendasi yang cukup relevan dengan tingkat akurasi dan cakupan yang seimbang. Namun, untuk film seperti _Jumanji_, meskipun rekomendasi memiliki cakupan penuh (_recall_ tinggi), ketepatan dalam memilih film-film yang sangat mirip masih memerlukan peningkatan.

Evaluasi ini menunjukkan pentingnya menggunakan kedua metrik dalam mengevaluasi rekomendasi berbasis konten agar model dapat memberikan rekomendasi yang sesuai dengan preferensi pengguna secara menyeluruh.

### Collaborative Filtering

### Langkah-Langkah

1. **Preprocessing Data**: Dataset MovieLens 100K disiapkan dengan memasukkan kolom `userId`, `movieId`, dan `rating`.
2. **Pemisahan Data**: Data dibagi menjadi data latih dan data uji dengan pembagian 80% untuk pelatihan dan 20% untuk pengujian menggunakan `train_test_split` dari library Surprise.
3. **Pelatihan Model**: Algoritma SVD diterapkan pada data latih untuk menemukan pola rating antar pengguna dan item.
4. **Evaluasi Model**: Model dievaluasi dengan menggunakan metrik evaluasi **Root Mean Squared Error (RMSE)** dan **Mean Absolute Error (MAE)** untuk mengukur kinerja prediksi model.

### Metrik Evaluasi

#### 1. Root Mean Squared Error (RMSE)

**RMSE** adalah metrik yang mengukur perbedaan antara nilai rating asli dengan nilai rating yang diprediksi oleh model. RMSE dihitung dengan rumus berikut:

RMSE = √( (1 / N) \* Σ(y_i - ŷ_i)^2 )

RMSE memberikan gambaran seberapa jauh, rata-rata, prediksi model dari nilai rating yang sebenarnya. Nilai RMSE yang lebih rendah menunjukkan bahwa model lebih akurat dalam memprediksi rating.

#### 2. Mean Absolute Error (MAE)

**MAE** adalah metrik yang mengukur rata-rata kesalahan absolut antara rating asli dan rating yang diprediksi. MAE dihitung dengan rumus berikut:

MAE = (1 / N) \* Σ|y_i - ŷ_i|

MAE menunjukkan rata-rata kesalahan prediksi tanpa memperhitungkan arah kesalahan (positif atau negatif). Seperti RMSE, nilai MAE yang lebih rendah menandakan bahwa model memiliki kinerja prediksi yang lebih baik.

### Alasan Penggunaan RMSE dan MAE

Dalam konteks rekomendasi film, baik RMSE maupun MAE relevan untuk mengukur kinerja model, karena keduanya menilai akurasi prediksi rating yang diberikan kepada film. RMSE memberikan bobot lebih besar pada kesalahan yang lebih besar, sehingga lebih sensitif terhadap prediksi yang meleset jauh dari nilai asli. Di sisi lain, MAE memberikan rata-rata kesalahan yang lebih stabil, membantu dalam mengukur prediksi yang lebih konsisten.

### Hasil Proyek Berdasarkan Metrik Evaluasi

- **RMSE**: 0.8790
- **MAE**: 0.6756

Nilai RMSE sebesar 0.8790 menunjukkan bahwa rata-rata kesalahan kuadrat dari prediksi model relatif kecil, yang menunjukkan bahwa model cukup akurat dalam memberikan prediksi rating. Nilai MAE sebesar 0.6778 menunjukkan rata-rata kesalahan absolut yang rendah, yang berarti model menghasilkan prediksi yang konsisten. Kedua metrik ini mengindikasikan bahwa model dapat memberikan rekomendasi film dengan cukup baik.

### Fungsi Rekomendasi

Fungsi `get_recommendations` digunakan untuk memberikan rekomendasi film kepada pengguna tertentu. Fungsi ini bekerja dengan:

1. Mengambil daftar film yang belum ditonton oleh pengguna.
2. Menghitung prediksi rating untuk film yang belum ditonton.
3. Mengurutkan film berdasarkan prediksi rating secara menurun dan memilih film dengan prediksi rating tertinggi.

Hasil dari fungsi ini adalah daftar 10 rekomendasi film teratas untuk pengguna berdasarkan preferensi pengguna serupa lainnya.
Sistem rekomendasi film berbasis collaborative filtering menggunakan SVD berhasil dibangun dan dievaluasi dengan RMSE dan MAE. Metrik evaluasi menunjukkan bahwa model memiliki akurasi prediksi yang baik, menjadikannya solusi yang efektif untuk memberikan rekomendasi film yang relevan kepada pengguna.

### Kesimpulan

Dengan mengembangkan sistem rekomendasi film menggunakan **Content-Based Filtering (Cosine Similarity)** dan **Collaborative Filtering (SVD)**, saya berhasil menjawab tantangan utama dalam sistem rekomendasi, yaitu:

1. **Mengatasi Pilihan yang Terlalu Banyak**: Sistem rekomendasi berbasis konten yang dibangun mampu menyaring pilihan film yang sesuai dengan preferensi spesifik pengguna, berdasarkan kesamaan atribut seperti genre atau aktor, sehingga membantu pengguna menemukan film yang paling relevan dengan minat mereka.

2. **Mengatasi Cold Start dan Sparsity**:

   - Masalah **cold start** diatasi dengan Content-Based Filtering, yang tidak bergantung pada banyaknya interaksi pengguna untuk memberikan rekomendasi awal.
   - Masalah **sparsity** pada dataset MovieLens 100K berhasil diatasi melalui implementasi SVD, yang secara efektif mengurangi dampak dari data yang terbatas dan meningkatkan akurasi rekomendasi.

3. **Mengoptimalkan Cosine Similarity dan SVD**:

   - **Cosine Similarity** dioptimalkan untuk menghitung kemiripan antar film pada Content-Based Filtering, sehingga sistem mampu menghasilkan rekomendasi yang akurat berdasarkan kesamaan fitur antar film.
   - **SVD** diterapkan dalam Collaborative Filtering untuk memaksimalkan efisiensi pada data rating yang sparse, meningkatkan akurasi rekomendasi dengan memprediksi rating yang tidak tersedia, dan meminimalkan dampak data yang kurang.

4. **Mencapai Tujuan Rekomendasi yang Personal dan Relevan**:
   - Kombinasi algoritma Content-Based dan Collaborative Filtering menghasilkan rekomendasi yang personal dan relevan bagi pengguna.
   - Sistem ini memberikan pengalaman yang lebih terfokus dan bervariasi, meningkatkan kepuasan dan keterlibatan pengguna dengan platform.

Dengan demikian, sistem yang dibangun ini mampu memberikan solusi efektif terhadap masalah **overwhelming choice**, **cold start**, dan **sparsity of data**, sekaligus mencapai tujuan untuk menyediakan rekomendasi film yang personal, akurat, dan relevan.
