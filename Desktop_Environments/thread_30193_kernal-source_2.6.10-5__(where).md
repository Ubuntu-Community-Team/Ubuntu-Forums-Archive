---
title: "kernal-source 2.6.10-5  (where?)"
date: 2005-04-27
forum: Desktop Environments
---

### Post by ljepava on 2005-04-27
Plz can some1 post FTP, where i can download kernal-source 2.6.10-5 for Kubuntu 5.04?
I have 56KB modem so I am not using apt-get
ill use some download manager with resume capatibility

---

### Post by nad on 2005-04-27
[ftp://archive.ubuntu.com/](ftp://archive.ubuntu.com/)

Have fun!

---

### Post by ljepava on 2005-04-27
so, i guess i have to download :    kernel-source-2.6.10_2.6.10-6_all.deb 
from       [ftp://archive.ubuntu.com/ubuntu/pool/universe/k/kernel-source-2.6.10/](ftp://archive.ubuntu.com/ubuntu/pool/universe/k/kernel-source-2.6.10/)

and then what,


dpkg - i kernel-source-2.6.10_2.6.10-6_all.deb      ????  am i right ???





                     
                                                        n00b                 ](*,)

---

### Post by nad on 2005-04-27
Yes. That will leave a bzipped tarball in /usr/src/. tar -xvvjf filename  will unpack it to linux-2.6.10 with verbose, verbose messages.

If you want to build anything, you will need the build-essentials package also as ubuntu doesn't come installed with a compiler and other odds and ends. This package is available on your disk. You ought to get the kernel-package package also which will make it easy to do it the debian way and will output deb packages ready for installation.

What are you planning on doing? You've got a lot of reading to do.

---

### Post by az on 2005-04-27
packages.ubuntu.com

For the full source, use the linux-tree package.  Yes, download it and then sudo dpkg -i <package-x-y-z.deb>


If you only need to build a module for your kernel, use the linux-headers.  The package is found on your cd.

install linux-headers-2.6.10-5 and build-essential with synaptic.  You should be able to build just about any module with just the headers.

---

### Post by ljepava on 2005-04-28
thx  guys
 \\:D/

---

### Post by ljepava on 2005-04-28
[QUOTE=nad]Yes. That will leave a bzipped tarball in /usr/src/. tar -xvvjf filename  will unpack it to linux-2.6.10 with verbose, verbose messages.

If you want to build anything, you will need the build-essentials package also as ubuntu doesn't come installed with a compiler and other odds and ends. This package is available on your disk. You ought to get the kernel-package package also which will make it easy to do it the debian way and will output deb packages ready for installation.

What are you planning on doing? You've got a lot of reading to do.[/QUOTE]


i needed kernal-source to install my modem (softmodem Conexant HSF)

---

### Post by nad on 2005-04-28
Good catch!

For those of you with conexant based winmodems ('software' modems), this page offers deb packages of necessary restricted binaries, source and scripts to build drivers.

[http://www.linuxant.com/drivers/hsf/full/downloads.php](http://www.linuxant.com/drivers/hsf/full/downloads.php)

---

### Post by shmk on 2005-06-07
[QUOTE=ljepava]i needed kernal-source to install my modem (softmodem Conexant HSF)[/QUOTE]
 You don't have to download all source, I installed it just with kernel-headers ;)

---

