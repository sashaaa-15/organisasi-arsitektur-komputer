# organisasi-arsitektur-komputer

![image](https://github.com/user-attachments/assets/7a66c1ad-3198-4072-b3b4-a26e2d37e8df)


section .data

huruf db 'Ayu Salsabilla'  ; Mendefinisikan karakter 'a' di bagian data

section .text
  
  global _start 

_start:

    mov     edx, 14             ; Panjang pesan (1 byte)
    mov     ecx, huruf          ; Alamat pesan (pointer ke 'a')
    mov     ebx, 1              ; File descriptor 1 (stdout)
    mov     eax, 4              ; Nomor sistem panggilan sys_write
    int     0x80                ; Memanggil kernel untuk menulis ke stdout
    mov     eax, 1              ; Nomor sistem panggilan sys_exit
    xor     ebx, ebx            ; Menetapkan status keluar (0)
    int     0x80                ; Memanggil kernel untuk keluar dari program

## Bagian Data
* section .data: Bagian ini digunakan untuk mendefinisikan data statis.
* huruf db 'Ayu Salsabilla': Mendeklarasikan sebuah variabel huruf yang menyimpan string "Ayu Salsabilla" sebagai byte data (db = define byte).
* Komentar menyatakan bahwa ini mendefinisikan karakter, meskipun sebenarnya menyimpan seluruh string, bukan hanya huruf 'a'.

## Bagian Kode
* section .text: Bagian untuk kode program.
* global _start: Mendeklarasikan bahwa _start adalah titik masuk (entry point) program.

## Fungsi Utama (Program Dimulai)
Ini adalah titik awal eksekusi program.

## Menulis ke stdout
Penjelasan:
* mov edx, 14: Panjang string "Ayu Salsabilla" adalah 14 karakter (termasuk spasi), jadi panjang pesan diatur ke 14 byte.
* mov ecx, huruf: Menunjukkan alamat memori dari string huruf.
* mov ebx, 1: File descriptor 1 adalah standar output (stdout).
* mov eax, 4: Nomor syscall 4 adalah sys_write.
* int 0x80: Memanggil interrupt 0x80 untuk meminta layanan sistem Linux (syscall).

Artinya, program ini menampilkan string "Ayu Salsabilla" ke layar.

## Keluar dari Program
Penjelasan:
* mov eax, 1: Nomor syscall 1 adalah sys_exit.
* xor ebx, ebx: Mengatur nilai ebx ke 0 (status keluar 0).
* int 0x80: Memanggil syscall untuk keluar dari program.
