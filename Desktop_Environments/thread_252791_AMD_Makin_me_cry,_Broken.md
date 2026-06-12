---
title: "AMD Makin me cry, Broken"
date: 2006-09-07
forum: Desktop Environments
---

### Post by rapollon on 2006-09-07
HI, 

I have 3 ubuntu machines, 1 server 2 clients, 

The Server is running a AMD-K6 450MHz processor, 
It runs perfect with Debian, but with Dapper it is so slow, can't even stream my music, a transfer of 38 music files took about an hour.  But, my small labtop a P1 Toshiba 7010CT 233MHz runs much quicker.  Why is that?



Server specs:
Processors	1
Model	AMD-K6(tm) 3D processor
Chip MHz	450.18 MHz
Cache Size	64 KB
System Bogomips	901.71
PCI Devices	0000:00:00.1 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:01.1 ff00: Silicon Integrated Systems [SiS] ACPI
0000:00:09.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone]
0000:00:0c.0 Multimedia audio controller: ESS Technology ES1969 Solo-1 Audiodrive
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 530/620 PCI/AGP VGA Display Adapter
IDE Devices	hda: Maxtor 85120A8 (Capacity: 4.77 GB)
hdc: LG CD-RW CED-8042B
hdd: Maxtor 91021U2 (Capacity: 9.42 GB)
SCSI Devices	HP Photosmart 8400 (Direct-Access)
USB Devices	Linux 2.6.15-26-386 ohci_hcd OHCI Host Controller 0000:00:01.2
HP Photosmart 8400 series CN5442108Z047X

---

### Post by lagagnon on 2006-09-07
How much RAM in each of those machines? Did you try the following commands to see what your system memory and CPU activity is?

df
fdisk -l
free
top 
ps aux

Post the output of those commands here.

---

### Post by rapollon on 2006-09-09
No, but, I can't understand how the P1 machine is running more efficiently than the PII @ 450MHz. I mean even browsing the internet in a task... it didn't do that on the Debian distro, why is that?

---

