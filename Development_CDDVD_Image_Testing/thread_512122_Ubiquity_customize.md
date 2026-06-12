---
title: "Ubiquity customize ??"
date: 2007-07-28
forum: Development CD/DVD Image Testing
---

### Post by booza on 2007-07-28
Hi,
last time i make a own live , with some changes, but when i install live cd with ubiquity then dont work the customize desktop ...like e17 or openbox . my question , how can i customize the installer ??

Greetz Booza

---

### Post by smartboyathome on 2007-07-29
I wouldn't know, but if you find out, please share!!! I may use that to make a DVD with GNOME, KDE, XFCE, (and if room) E17.

---

### Post by booza on 2007-07-29
@smartboyathome

for your "Project" you dont need , to change so much ,  a made a "MutibootDVD" for a long time ;)

Sorry for my bad english ,but i hope you understand that :)

First you need , from evevery ubuntu distro a iso ( i take a 32 and 64 bit iso)


Then create  a Multiboot folder ! 
Then in this folder a 32 and 64 bit folder !!

Then but all files from the iso , in the right folder ..32 bit in 32bit ......

Then copy the isolinux folder from ...32 bit version in the Multiboot foler -> look like that 

-Multiboot folder
               -32bit folder
               -64bit folder
               -isolinux folder

In the isolinux folder, you must custumize the isolinux.cfg its easy ;)

bsp.:

    DEFAULT /Ubuntu32bit/casper/vmlinuz
GFXBOOT bootlogo
GFXBOOT-BACKGROUND 0xB6875A
APPEND  file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/32bit/casper/initrd.gz quiet splash --

LABEL live-32-bit
  menu label ^Start or install Ubuntu-32bit
  kernel /32bit/casper/vmlinuz
  append  file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/32bit/casper/initrd.gz quiet splash --

LABEL live-64-bit
  menu label ^Start or install Ubuntu-64bit
  kernel /64bit/casper/vmlinuz
  append  file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/64bit/casper/initrd.gz quiet splash --

LABEL xforcevesa-32-bit
  menu label Start Ubuntu-32bit in safe ^graphics mode
  kernel /32bit/casper/vmlinuz
  append  file=/cdrom/preseed/ubuntu.seed boot=casper xforcevesa initrd=/32bit/casper/initrd.gz quiet splash --

LABEL xforcevesa-64-bit
  menu label Start Ubuntu-64bit in safe ^graphics mode
  kernel /64bit/casper/vmlinuz
  append  file=/cdrom/preseed/ubuntu.seed boot=casper xforcevesa initrd=/64bit/casper/initrd.gz quiet splash --

LABEL check
  menu label ^Check CD for defects
  kernel /32bit/casper/vmlinuz
  append  boot=casper integrity-check initrd=/32bit/casper/initrd.gz quiet splash --
LABEL memtest
  menu label ^Memory test
  kernel /32bit/install/mt86plus
  append -
LABEL hd
  menu label ^Boot from first hard disk
  localboot 0x80
  append -


DISPLAY isolinux.txt
TIMEOUT 300
PROMPT 1
F1 f1.txt
F2 f2.txt
F3 f3.txt
F4 f4.txt
F5 f5.txt
F6 f6.txt
F7 f7.txt
F8 f8.txt
F9 f9.txt
F0 f10.txt


Last step : sudo mkisofs -r -N -ldots -d -D -J -V “Multiboot” -b isolinux/isolinux.bin -c isolinux/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table -x lost+found -o /home/USER/multiboot.iso /home/USER/Desktop/Multiboot/

(Change USER)

Thats all , you foun the Multiboot iso in your home folder :D

Screenshot : [http://http://www.spongedpics.com/upload/WK1180472683W465c956b4277d-bootscreen.bmp]("http://http://www.spongedpics.com/upload/WK1180472683W465c956b4277d-bootscreen.bmp")

Greetz Booza

---

### Post by smartboyathome on 2007-07-29
Thanks! I will try this when I have some time! ^_^

---

### Post by gosalia on 2010-01-01
Hello, I am sorry if this is waaaaay too late of a reply but I know how to customize the Ubiquity Installation. Check out my Tutorial here...

[http://ubuntuforums.org/showthread.php?p=8591740#post8591740](http://ubuntuforums.org/showthread.php?p=8591740#post8591740)

---

