---
title: "[Guide] How to Play Halo Evolved on DEBIAN/Ubuntu/SID"
date: 2022-07-30
forum: Gaming &amp; Leisure
---

### Post by patrick2957672 on 2022-07-30
Hello,

A little work around to play Halo Evolved on PC, using the x86/i386/686 PAE kernel.
My Notebook is a eeePC Asus, intel. 

First, take a older general of Linux Ubuntu with 686 PAE Kernel.
See Ubuntu Archive FTP/HTTP server.

I usually boot ubuntu from Grub with : 
```
menuentry 'Linux Ubuntu 686' --class gnu-linux --class gnu { 
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos4'
        linux   /boot/vmlinuz-4.9.0-11-686 root=/dev/sda4 rw 
        initrd  /boot/initrd.img-4.9.0-11-686
}

```

debootstrap a debian i386 or install a i386/686 ubuntu on the target partition.

**1.) install wine**

```
 sudo apt-get update
 sudo apt-get install wine 

```

**2.) create ~/.wine **

```
 winecfg

```

**3.) Mount CD**


384fb2afa7815109a7e06a3e43bcb092  HALO.iso

Mount the cdrom to /media/cdrom, with :

```
mkdir /media/cdrom ; mount HALO.iso /media/cdrom 

```


[B]4.) Copy mfc42 dll and pidgen.dll

[/B]Copy the files mfc42 and pidgen.dll into ~/.wine/drive_c/windows/system32

6bc8b5736ba5537b3bbd0746ba508f46  pidgen.dll
8d0dbf25d91aa1be1e4e348434fd12e4  mfc42.dll
acf4dcccef25f9213a11bb88e9be2fac  mfc42u.dll

[B]5.) Install Halo Evolved

[/B]```
 cd /media/cdrom ; wine Setup 

```[B]

6) [/B][B]Patch Halo Evolved with

[/B][https://web.archive.org/web/20180605162448if_/http://halo.bungie.net/images/games/halopc/patch/110/halopc-patch-1.0.10.exe](https://web.archive.org/web/20180605162448if_/http://halo.bungie.net/images/games/halopc/patch/110/halopc-patch-1.0.10.exe)

[B]7.) Once done, Play it and have fun

[/B]cd ; cd .wine/drive_c/"Program Files" ... halo folder and type :   wine halo.exe

---

