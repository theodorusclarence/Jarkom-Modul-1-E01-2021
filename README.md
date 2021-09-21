# Jarkom-Modul-1-E01-2021

- Clarence 05111940000104
- Nur Putra Khanafi 05111940000020
- Husnan 05111940007002

## 1 
> Sebutkan webserver yang digunakan pada "ichimarumaru.tech"! 

## 2 
> Temukan paket dari web-web yang menggunakan basic authentication method! 

## 3 
> Ikuti perintah di basic.ichimarumaru.tech! Username dan password bisa didapatkan dari file .pcapng!

## 4 
> Temukan paket mysql yang mengandung perintah query select!

## 5 
> Login ke portal.ichimarumaru.tech kemudian ikuti perintahnya! Username dan password bisa didapat dari query insert pada table users dari file .pcap!

## 6 
> Cari username dan password ketika melakukan login ke FTP Server!

Sesuai dengan referensi, default port FTP server adalah port 21

![image](https://user-images.githubusercontent.com/55318172/134176792-8c99257d-e8f7-4016-b6c8-fb7f0c3af975.png)

Maka, kami menggunakan `ftp && tcp.port == 21` pada Display Filter. Kemudian kami mengecek paket yang memiliki informasi user

![image](https://user-images.githubusercontent.com/55318172/134177389-a2d53bc5-d6b4-4076-b012-e3fac24e9832.png)

Ketika dicek, didapatkan user: **secretuser** pada FTP Request arg

Kemudian kami juga mengecek password, 

![image](https://user-images.githubusercontent.com/55318172/134177590-685128e1-9418-4881-abbf-8d2f8bdb4362.png)

Ketika dicek, didapatkan password: **aku.pengen.pw.aja** pada FTP Request arg

Maka, username:password = **secretuser:aku.pengen.pw.aja**

## 7 
> Ada 500 file zip yang disimpan ke FTP Server dengan nama 0.zip, 1.zip, 2.zip, ..., 499.zip. Simpan dan Buka file pdf tersebut. (Hint = nama pdf-nya "Real.pdf")

Pertama, karena ingin mencari file yang bernama Real.pdf pada FTP Server, maka kami menggunakan display filter yaitu `ftp-data contains "Real.pdf`. Kemudian kami `Follow > TCP Stream`

![image](https://user-images.githubusercontent.com/55318172/134177771-e4103a9b-27b2-4c60-8a45-32902b7f2887.png)

Dari Follow TCP Stream tersebut kita dapat menyimpan file as **Raw**, dan dinamakan dengan ekstensi `.zip`

![image](https://user-images.githubusercontent.com/55318172/134177908-2d72ea41-a623-4604-9f5b-c7a48a7dfc6f.png)

Kemudian, file tersebut bisa langsung diunzip dan ketika dibuka tampilannya sebagai berikut

![image](https://user-images.githubusercontent.com/55318172/134177984-cc17aef8-9c15-45d2-8996-b136f265323c.png)

## 8 
> Cari paket yang menunjukan pengambilan file dari FTP tersebut!

Karena pengambilan data dari FTP, maka kita bisa menggunakan command yang mirip dengan nomor 7, dengan mencari pengambilan file yaitu `RETR`, maka pada Display Filter dapat dicari `ftp-data.command contains RETR`.

![image](https://user-images.githubusercontent.com/55318172/134178149-fde8c90d-4260-4559-83a3-2c60051d5dc4.png)

## 9 
> Dari paket-paket yang menuju FTP terdapat inidkasi penyimpanan beberapa file. Salah satunya adalah sebuah file berisi data rahasia dengan nama "secret.zip". Simpan dan buka file tersebut!

Pada nomor 9, kami menggunakan `ftp-data.command contains secret.zip` untuk mencari file, kemudian menyimpan menggunakan `Follow > TCP Stream`, save as raw.

![image](https://user-images.githubusercontent.com/55318172/134178365-6e3eafaf-e075-4770-8b3b-93190697aec6.png)

Ketika kami buka file `.zip` tersebut di lock, maka kami mencari ke nomor 10, dan mendapatkan password: **d1b1langbukanapaapajugagapercaya**, dan mengunzip file dengan password tersebut.

![image](https://user-images.githubusercontent.com/55318172/134178613-14e85f1d-9382-4827-9253-b6661cbd82a7.png)

Kemudian kami setelah berhasil di unzip, terdapat pdf sebagai berikut

![image](https://user-images.githubusercontent.com/55318172/134178669-7a6a5573-499a-47fe-98fc-63f54a9cd257.png)


## 10
>  Selain itu terdapat "history.txt" yang kemungkinan berisi history bash server tersebut! Gunakan isi dari "history.txt" untuk menemukan password untuk membuka file rahasia yang ada di "secret.zip"!

Karena kita ingin mencari "history.txt" pada FTP, maka kita bisa menambahkan `ftp-data.command contains history.txt` pada Display Filter

![image](https://user-images.githubusercontent.com/55318172/134178799-8e82f498-2cef-44fd-b9d7-457342a855b4.png)

Setelah di `Follow > TCP Stream` maka didapat history bash script yang pada line 289 berarti menyimpan baris terakhir dari `bukanapaapa.txt` dan digunakan untuk membuka zip nomor 9.

Maka, kami mencari file `bukanapaapa.txt` dengan Display Filter `ftp-data.command contains bukanapapa.txt`

![image](https://user-images.githubusercontent.com/55318172/134179324-082685d1-465f-4ee9-9a42-deade35ecb37.png)

Dari `Follow > TCP Stream`, atau menjalankan bash script line 289,

![image](https://user-images.githubusercontent.com/55318172/134179389-0652ea32-4bbc-49b3-8fa8-98c88163320b.png)

Didapat password yaitu **d1b1langbukanapaapajugagapercaya**

## 11
>  Filter sehingga wireshark hanya mengambil paket yang berasal dari port 80!

## 12
>  Filter sehingga wireshark hanya mengambil paket yang mengandung port 21!

## 13
>  Filter sehingga wireshark hanya menampilkan paket yang menuju port 443!

## 14
>  Filter sehingga wireshark hanya mengambil paket yang tujuannya ke kemenag.go.id!

## 15
>  Filter sehingga wireshark hanya mengambil paket yang berasal dari ip kalian!

