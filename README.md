# Tugas 1 Komunikasi Data dan Jaringan Komputer

| Nama                          | NRP        |
|-------------------------------|------------|
| Putu Yudi Nandanjaya Wiraguna | 5027241080 |

Yayasan Pendidikan ARA akan membangun jaringan untuk beberapa unit kerja. Sebagian unit berada di kantor pusat, sedangkan Bidang Pengawas Sekolah berada di kantor cabang. IP yang bisa digunakan 

### Kantor Pusat

| **Ruang**                        | **Jumlah Host Aktif** |
| -------------------------------- | --------------------- |
| Bidang Guru & Tendik             | 95 host               |
| Bidang Kurikulum                 | 220 host              |
| Bidang Sarana Prasarana          | 45 host               |
| Bidang Pengawas Sekolah (Branch) | 18 host               |
| Server & Admin                   | 6 host                |
| Sekretariat                      | 380 host              |


### Kantor Cabang

| **Ruang**               | **Jumlah Host Aktif** |
| ----------------------- | --------------------- |
| Bidang Pengawas Sekolah | 18 host               |

1. Rancanglah topologinya menggunakan Cisco Packet Tracer.
2. Setiap mahasiswa memiliki base network unik, dengan aturan: 
`10.(NRP mod 256).0.0`
**NRP 5027241080 mod 256 = 120, maka base: 10.120.0.0.**
3. Lakukan perhitungan subnetting dengan VLSM & CIDR di Spreadsheet untuk seluruh jaringan LAN dan link antar-router.
4. Konfigurasikan alamat IP di setiap interface router dan host pada CPT sesuai tabel hasil subnetting di Spreadsheet.


## Topologi 

<img width="1014" height="670" alt="image" src="https://github.com/user-attachments/assets/a7e63c9e-705f-4e8f-8548-2359ac167f80" />

## Subneting

IP Prefix : 10.120.0.0/22
Total host : 778 host

| Subnet                           | Kebutuhan Host | Netmask |
| -------------------------------- | -------------- | ------- |
| Sekretariat                      | 381 host       | /23     |
| Bidang Kurikulum                 | 221 host       | /24     |
| Bidang Guru & Tendik             | 96 host        | /25     |
| Bidang Sarana Prasarana          | 46 host        | /26     |
| Bidang Pengawas Sekolah          | 19 host        | /27     |
| Server & Admin                   | 7 host         | /28     |
| Interlink                        | 6 host         | /29     |
| Link WAN (Pusat–Cabang)          | 2 host         | /30     |
| **TOTAL**                        | **778 host**   | **/22** |

<img width="1232" height="670" alt="Screenshot 2025-11-11 140610" src="https://github.com/user-attachments/assets/ba452566-6136-4535-9ebb-dd6b03d6421c" />


## Perhitungan Subnetting VLSM

<img width="888" height="631" alt="image" src="https://github.com/user-attachments/assets/ee959d27-8e3e-4d06-8948-eae9a6d22c7e" />


| Subnet / Departemen     | Kebutuhan Host | Bit Host | Host Usable | Network      | Prefix | Range Block | Netmask         | Gateway      | Broadcast    | Rentang IP yang Dapat Dipakai |
| ----------------------- | -------------- | -------- | ----------- | ------------ | ------ | ----------- | --------------- | ------------ | ------------ | ----------------------------- |
| Sekretariat             | 381            | 9        | 510         | 10.120.2.0   | /23    | 512         | 255.255.254.0   | 10.120.2.1   | 10.120.3.255 | 10.120.2.1 - 10.120.3.254     |
| Bidang Kurikulum        | 221            | 8        | 254         | 10.120.1.0   | /24    | 256         | 255.255.255.0   | 10.120.1.1   | 10.120.1.255 | 10.120.1.1 - 10.120.1.254     |
| Bidang Guru & Tendik    | 96             | 7        | 126         | 10.120.0.128 | /25    | 128         | 255.255.255.128 | 10.120.0.129 | 10.120.0.255 | 10.120.0.129 - 10.120.0.254     |
| Bidang Sarana Prasarana | 46             | 6        | 62          | 10.120.0.64  | /26    | 64          | 255.255.255.192 | 10.120.0.65  | 10.120.0.127 | 10.120.0.65 - 10.120.0.126   |
| Bidang Pengawas Sekolah | 19             | 5        | 30          | 10.120.0.32  | /27    | 32          | 255.255.255.224 | 10.120.0.33  | 10.120.0.63  | 10.120.0.33 - 10.120.0.62   |
| Server & Admin          | 7              | 4        | 14          | 10.120.0.16  | /28    | 16          | 255.255.255.240 | 10.120.0.17  | 10.120.0.31  | 10.120.0.17 - 10.120.0.30  |
| Interlink Kantor Pusat  | 6              | 3        | 6           | 10.120.0.8   | /29    | 8           | 255.255.255.248 | 10.120.0.9   | 10.120.0.15 | 10.120.0.9 - 10.120.0.14   |
| Link WAN (Pusat–Cabang) | 2              | 2        | 2           | 10.120.0.0   | /30    | 4           | 255.255.255.252 | Pusat : 10.120.0.1 / Cabang : 10.120.0.2 | 10.120.0.3 | 10.120.0.1 - 10.120.0.2   |

## Agregasi CIDR / Supernetting 

| Keterangan            | Nilai                       |
| --------------------- | --------------------------- |
| **Network Address**   | `10.120.0.0`                |
| **Subnet Mask**       | `255.255.252.0`             |
| **Prefix (CIDR)**     | `/22`                       |
| **Range Host**        | `10.120.0.1 - 10.120.3.254` |
| **Broadcast Address** | `10.120.3.255`              |
| **Gateway**           | `N/A`                       |



