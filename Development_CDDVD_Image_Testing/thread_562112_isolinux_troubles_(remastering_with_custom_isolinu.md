---
title: "isolinux troubles (remastering with custom isolinux.cfg)"
date: 2007-09-28
forum: Development CD/DVD Image Testing
---

### Post by BrandonPerry on 2007-09-28
Hi, I am creating a custom LiveCD for use at work with several specific uses (diagnostics and repair mainly). I am using memdisk to load a DOS based drive diagnostic tool (the drive fitness test), though I have never done this before and have only gotten about part of the way with this. I am using an ISO of the disk image of the drive fitness test (not sure if you can do this or not) and memdisk starts to load the drive test, but freezes at a "Loading boot sector... booting...". :confused: 

Do I need to extract the contents of the ISO? I have tried that in the past, but there would be nothing to boot to if I did. Here is my isolinux.cfg...

    DEFAULT /casper/vmlinuz
GFXBOOT bootlogo
GFXBOOT-ACCESS-OPTIONS v2 v3 m2
APPEND  file=/cdrom/preseed/xubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
LABEL live
  menu label ^Start or install Xubuntu
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/xubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
LABEL clamav_ide
  menu label Start a virus scan with ClamAV -- IDE
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/clamav_ide.seed boot=casper initrd=/casper/initrd.gz quiet splash --
LABEL drivetest
  menu label Start ^Drive Fitness Test
  kernel /install/memdisk
  append initrd=/install/dft32_v410_b00.iso
LABEL memtest
  menu label ^Memory test
  kernel /install/mt86plus
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

---

### Post by MrFSL on 2007-09-28
> load a DOS based drive diagnostic tool (the drive fitness test),

So let me get this straight - you have ALREADY got a bootable CDROM that boots this "Drive Fitness Test"? If that is the case then you will need to take the contents off the disk.

> Do I need to extract the contents of the ISO? I have tried that in the past, but there would be nothing to boot to if I did. Here is my isolinux.cfg...
...Sure there would! That's what isolinux is... a bootloader. The question is, what exactly is on your cdrom/in your iso image? Is it a floppy emulated boot image or what? Let me know what is in your iso image and maybe I can help.

---

### Post by BrandonPerry on 2007-09-28
Inside the ISO is a copy of IBMDOS (IBMBIO.COM, IBMDOS.COM and all the DOS drivers) as well as the actual drive test program. I have tried setting initrd=/install/IBMDOS.COM when it was unpacked, but it always said it didn't exist for some reason...

---

### Post by BrandonPerry on 2007-09-28
I figured out what I had to do. There is also an available floppy image for download. I downloaded that and replaced the iso with the img and it booted fine, thanks for the help!

---

