#include <iostream>
#include <conio.h>
#include <cstring>
#include <limits>
#define max 20
using namespace std;

//Mengunaan Struct
struct queue
{
    int head, tail;
    char data [20][20];
};

//Pembuatan objek dari suatu kelas
    queue nama, pesanan;

//Fungsi untuk pilihan
void inisial()
{
    nama.head=nama.tail=-1;
    pesanan.head=pesanan.tail=-1;
}

// --- QUEUE ---
int isFull()
{
    if(nama.tail == max-1)
    return 1;
    else
    return 0;
}
int isEmpty()
{
    if (nama.tail == -1)
    {
        nama.head = -1;
        return 1;
    }
    else
    return 0;
}
void enqueue(char d[20])
{
    system("cls");
    nama.head=0;
    nama.tail++;
    strcpy (nama.data[nama.tail],d);
}
void enqueue_2(char d[20])
{
    system("cls");
    pesanan.head=0;
    pesanan.tail++;
    strcpy (pesanan.data[pesanan.tail],d);
}
void dequeue()
{
    system("cls");
    cout << "Pesanan " << pesanan.data[pesanan.head] << " atas nama " << nama.data[nama.head] << " sudah dilayani" << endl;
    for (int i = nama.head; i <= nama.tail; i++)
    strcpy (nama.data[i], nama.data[i+1]);
    nama.tail--;
    for (int i = pesanan.head; i <= pesanan.tail; i++)
    strcpy (pesanan.data[i], pesanan.data[i+1]);
    pesanan.tail--;
}
void Reset()
{
    system ("cls");
    nama.head = nama.tail = -1;
    pesanan.head = pesanan.tail = -1;
    cout << "Seluruh daftar antrian telah dihapus" << endl;
}
void LK()
{
    cout << endl;
}
void garis ()
{
    cout << "===================================================" << endl;
}
void menu()
{
    cout << "================= Asian Food Menu =================" << endl;
    cout << "1. Paket1 (Bebek Peking + Nasi + Es Teh Manis)" << endl;
    cout << "2. Paket2 (Chicken Nanking + Nasi + Es Teh Manis" << endl;
    cout << "3. Paket3 (Ayam Kremes Serai Terasi + Nasi + Es Teh Manis) " << endl;
    cout << "4. Daebak1 (Dakgangjeon Rice bowl + Telur Goreng + Kimchi + Jus" << endl;
    cout << "5. Deabak2 (Chicken Ramyeon + Tteokbokki Mini + Kimchi + Jus" << endl;
    cout << "6. Dobu1 (Chicken Katsu Donburi + Orange" << endl;
    cout << "7. Dobu2 (Beef Teriyaki Donburi + Orange" << endl;
    garis();
}
    int main()
{
    int pilihan;
    inisial();
    char x[50], y[50];
    do
{
    cout << "============== Manu pilihan Program ===============" << endl;
    cout << "1. Daftar Menu Paket" << endl;
    cout << "2. Membuat Pesanan" << endl;
    cout << "3. Selesai melayani antrian" << endl;
    cout << "4. Menghapus seluruh daftar antrian" << endl;
    cout << "5. Keluar" << endl;
    garis();
    LK();
    cout << "Antrian yang Dimiliki: " << endl;
    if (nama.tail == -1)
{
    cout << "Tidak Ada" << endl;
}
else
{
    for (int i=0; i <= nama.tail; i++)
    cout << i+1 << ". " << nama.data[i] << " dengan paket pesanan: " << pesanan.data[i] << endl;
}
    LK();
        cout << "Masukkan Pilihan: ";
        cin >> pilihan;
    LK();
        switch (pilihan)
{
    case 1:
        menu();
        LK();
    break;
    case 2:
    if (!isFull())
{
    cout << "Note: Gunakan nama depan atau panggilan" << endl;
    cout << "Nama Pemesan : ";
    cin >> x;
LK();
    cout << "Note: Gunakan nama paket, jika lebih dari satu bisa'Do1,Pa1,Da2'" << endl;
    cout << "Paket makanan yang dipesan: ";
    cin >> y;
enqueue(x);
enqueue_2(y);
}
else
    cout << "Antrian Sudah Penuh!!!" << endl;
LK();
    break;
    case 3:
    if(!isEmpty())
dequeue();
else
    cout << "Antrian Masih Kosong!" << endl;
LK();
    break;
    case 4:
Reset();
LK();
    break;
    case 5:
        cout << "Tekan Enter untuk keluar" << endl;
    break;
    default:
LK();
    cout << "INPUT YANGA ANDA MASUKKAN SALAH!!!" << endl;
    cout << "== Tekan Space / Enter Kembali ==";
getch ();
system ("cls");
}
}
    while (pilihan !=5);
}
