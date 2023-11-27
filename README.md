# Check_pin_number_with_arduino_mega
![foto 1](https://github.com/sembre/Check_pin_number_with_arduino_mega/assets/4026499/16a19fe5-6835-4c86-a4de-edb14037d81a)

Program menggunakan modul TM1637 dan Arduino untuk memeriksa pin tertentu yang terhubung ke ground. Jika pin terhubung, angka sesuai indeks ditampilkan di display 7-segment.
Modul TM1637 ini biasanya digunakan untuk tampilan angka atau teks sederhana pada perangkat elektronik.

Berikut adalah penjelasan fungsi dan deskripsi dari kode tersebut:

# Pengaturan Pin dan Inisialisasi:

Kode #include <TM1637Display.h> mengimpor pustaka (library) TM1637Display yang digunakan untuk mengendalikan modul TM1637.
#define CLK_PIN A0 dan #define DIO_PIN A1 mendefinisikan pin CLK (Clock) dan DIO (Data Input/Output) untuk komunikasi dengan modul TM1637.
TM1637Display tm1637(CLK_PIN, DIO_PIN); inisialisasi objek tm1637 dari kelas TM1637Display dengan menggunakan pin CLK dan DIO yang telah didefinisikan sebelumnya.
Deklarasi Pin:

Array pins[] berisi daftar pin yang akan diperiksa untuk melihat apakah ada sinyal yang masuk (dihubungkan ke ground/GND).
Fungsi setup():

Di dalam fungsi setup(), modul TM1637 diinisialisasi dengan kecerahan (brightness) 7 (nilai dapat diatur antara 0 hingga 7) menggunakan tm1637.setBrightness(7);.
Selanjutnya, seluruh pin dalam array pins[] diatur sebagai input dengan internal pull-up resistor menggunakan pinMode(pins[i], INPUT_PULLUP);.
Fungsi loop():

Di dalam loop utama (loop()), setiap pin dalam array pins[] diperiksa satu per satu.
Jika pin tersebut memiliki sinyal rendah (LOW), artinya pin tersebut terhubung ke ground (GND), maka angka yang sesuai akan ditampilkan pada modul TM1637 selama 1 detik menggunakan tm1637.showNumberDecEx(valueToShow);. Nilai angka yang ditampilkan dihitung berdasarkan indeks pin dalam array.
Setelah 1 detik, tampilan dihapus menggunakan tm1637.clear();.
Setelah menemukan pin yang terhubung, loop dihentikan menggunakan break;.
Jadi, tujuan dari kode ini adalah untuk memeriksa setiap pin yang terdaftar dalam array pins[], dan jika ada pin yang terhubung ke ground, maka angka yang sesuai akan ditampilkan pada display 7-segment menggunakan modul TM1637. Setelah 1 detik, tampilan akan dihapus. Kode ini berguna untuk mendeteksi apakah ada input sinyal dari beberapa pin yang terhubung ke ground pada mikrokontroler Arduino.
