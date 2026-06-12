---
title: "need help extracting .img"
date: 2009-03-02
forum: General Help
---

### Post by rhyz on 2009-03-02
rhys@rhys-laptop:~$ sudo mount -t iso9660 -o loop '/home/rhys/Desktop/w98.img' '/home/rhys/Desktop/win98' 
[sudo] password for rhys: 
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

rhys@rhys-laptop:~$ 

This is the error i get when i try to mount the the img file into a folder is there anything i can do to extract the contents?

programme, terminal command

please help :)

---

### Post by rhyz on 2009-03-03
Anyone know how i can extract the img file

ANY IDEAS THANKS

---

### Post by taurus on 2009-03-03
Download a little program called img2iso.  Build it and install it on your machine.  Then, convert your filename.img to filename.iso and mount it again.

[http://www.t2-project.org/packages/img2iso.html](http://www.t2-project.org/packages/img2iso.html)

---

### Post by rhyz on 2009-03-04
thanks for info downloaded isodump-0.06.00

please help me build and install the programme :) never done before

---

### Post by philinux on 2009-03-04
There is also a ubuntu package.
[http://www.getdeb.net/search.php?keywords=acetoneiso](http://www.getdeb.net/search.php?keywords=acetoneiso)

---

