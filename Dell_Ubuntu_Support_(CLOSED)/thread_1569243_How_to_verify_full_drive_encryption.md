---
title: "How to verify full drive encryption?"
date: 2010-09-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ubto66 on 2010-09-06
Installationmedia:
Ubuntu 10.04.1 alternate 32 bit.
Installed on usb memory stick 16gb.
User not Ubuntu skilled.
Goal to verify that everything is encrypted.

Please only answer me, if you manage this field.
Members who want to discuss wheather full hard drive encryption is appropriate,
please don't answer.

Before answering please read this webpage, the part about B) thorough method encryption verification.
[http://rationallyparanoid.com/articles/ubuntu-10-lts-security.html](http://rationallyparanoid.com/articles/ubuntu-10-lts-security.html)

I have managed to install ubuntu 10.04.1 in full hard drive encryption mode on a usb
memory stick.
It took many hours, maybe because of the encryption proces and low speed 
usb stick.
There where no error prompts during installation, and the OS is runing like it is supposed to do.
When turning on the computer a preboot prompt asks for the password.

I don't know how to run root on ubuntu, so I ran the verification proces B) thorough method
described on the mentioned webpage, in sudo mode.

These were the results: 
bu@max1xx:~$ sudo fdisk -l
[sudo] password for ubu:
Disk /dev/sda: 16.0 GB, 16026435072 bytes
64 heads, 32 sectors/track, 15283 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006e710
Device Boot Start End Blocks Id System
/dev/sda1 * 2 244 248832 83 Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2 245 15283 15398913 5 Extended
Partition 2 does not end on cylinder boundary.
/dev/sda5 246 15283 15398912 83 Linux
ubu@max1xx:~$ sudo df -h
Filesystem Size Used Avail Use% Mounted on
/dev/mapper/max1xx-root
14G 2,4G 11G 19% /
none 874M 292K 873M 1% /dev
none 881M 1,4M 879M 1% /dev/shm
none 881M 84K 880M 1% /var/run
none 881M 0 881M 0% /var/lock
none 881M 0 881M 0% /lib/init/rw                             XXX
/dev/sda1 228M 21M 195M 10% /boot
ubu@max1xx:~$ sudo pvdisplay -m
--- Physical volume ---
PV Name /dev/mapper/sda5_crypt
VG Name max1xx
PV Size 14,68 GiB / not usable 1020,00 KiB
Allocatable yes (but full)
PE Size 4,00 MiB
Total PE 3759
Free PE 0
Allocated PE 3759
PV UUID YS7VP0-UVHZ-GUM3-4Syz-gxh4-PBNr-PobEeb
--- Physical Segments ---
Physical extent 0 to 3588:
Logical volume /dev/max1xx/root
Logical extents 0 to 3588
Physical extent 3589 to 3758:
Logical volume /dev/max1xx/swap_1
Logical extents 0 to 169                                              YYY
ubu@max1xx:~$ sudo lvdisplay -m
--- Logical volume ---
LV Name /dev/max1xx/root
VG Name max1xx
LV UUID dHPePu-gvBk-pJG0-udWq-fdPY-XrED-dL30kL
LV Write Access read/write

LV Status available
# open 1
LV Size 14,02 GiB
Current LE 3589
Segments 1
Allocation inherit
Read ahead sectors auto
- currently set to 256
Block device 252:1
--- Segments ---
Logical extent 0 to 3588:
Type linear
Physical volume /dev/mapper/sda5_crypt
Physical extents 0 to 3588
--- Logical volume ---
LV Name /dev/max1xx/swap_1
VG Name max1xx
LV UUID cTdACI-l01H-7orj-9NEs-rIXG-jXpZ-gHGI0h
LV Write Access read/write
LV Status available
# open 1
LV Size 680,00 MiB
Current LE 170
Segments 1
Allocation inherit
Read ahead sectors auto
- currently set to 256
Block device 252:2
--- Segments ---
Logical extent 0 to 169:
Type linear
Physical volume /dev/mapper/sda5_crypt
Physical extents 3589 to 3758
ubu@max1xx:~$ sudo cryptsetup status sda5_crypt
/dev/mapper/sda5_crypt is active:
cipher: aes-cbc-essiv:sha256
keysize: 256 bits
device: /dev/sda5
offset: 2056 sectors
size: 30795768 sectors
mode: read/write
ubu@max1xx:~$

Apart from the different size numbers I noticed that this line:
"none ...  ...  ...  ..  /var/lib/ureadahead/debugfs" is missing in my verification, see
my "XXX" mark. Does that mean anything?

At my "YYY" mark there is no "physical extent ... to ... :FREE.

If you know about this, please tell me if the encryption is ok.
Maybe explain some importen points.
I can't find out whether the swap volume is encrypted.

Thank you.

---

