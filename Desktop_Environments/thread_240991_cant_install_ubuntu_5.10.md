---
title: "cant install ubuntu 5.10"
date: 2006-08-21
forum: Desktop Environments
---

### Post by alon on 2006-08-21
Hi

im new in this whole linux thing...
a friend recommended me on cheking out Ubuntu. so i tried to...
i downloaded ubuntu 6.06 . tried to install it but i had the mounting root file system error , which no one could solve as i saw on many forums. i tried ver 6.06.1 and the same error appeared.

so i tried ver 5.10 . after choosing a language , location and keyboard layout , the installation loads something quite quick - approx 5 seconds delay , then i get a blue screen i think with a grey line at the bottom. nothing happens. no HDD , no CD reading. nothing.
i pressed the keyboard , random keys , and they appeared at the bottom grey line. like a text box. WTF? thats it. nothing happens.
i've tried 2 install 3 different versions of ubuntu and they all failed?!
my pc never caused me a single problem:

p4 2.6 HT
Asus p4p800
creative audigy 2 zs
maxtor 80g sata
corsair ddr400 2*256
leadtek geforce 5 5600 256mb


i'll appreciate any suggestion...

Alon

---

### Post by tuxcantfly on 2006-08-21
have you tried the dapper alternate install disk?

(I'll assume you were using the desktop one)

did the desktop disk fail on booting in live mode, or booting after installation?

have you tried using a different filesystem? (I'd reccomend reiserfs)

---

### Post by alon on 2006-08-21
sorry about the noob question - but whats the differences between dapper and ubuntu?

---

### Post by tuxcantfly on 2006-08-21
if all fails, you can use the ultra-new, edgy eft daily build

[http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

warning: highly experimental, you should try installing dapper from an alternate install disk first

---

### Post by tuxcantfly on 2006-08-21
dapper is ubuntu's latest release (6.06) codename

---

### Post by tuxcantfly on 2006-08-21
edgy is the next release's (6.10) codename, while 5.10 is breezy, 5.04 is hoary, and 4.10 is warty

---

### Post by alon on 2006-08-21
i downloaded and tried to install the intallation version , not the live one.
and what's reiserfs? i know only fat and ntfs
i've got a lot to learn....

---

### Post by alon on 2006-08-21
ok..........
i tried dapper , it has a serious bug appearantly (too many users have the mounting root file system error)
i dont want to install 6.10 cause u said it yourself - its experimental...
shoud i try 5.04?
is there something im doing wrong? i dont understand why didnt 5.10 worked out for me...

---

### Post by tuxcantfly on 2006-08-21
well, try the desktop disk then. does it boot at all?

as for reiserfs, it might help with your mounting root problem, which may be caused by ext3 (default ubuntu filesytem)

---

### Post by tuxcantfly on 2006-08-21
[http://ubuntu-releases.cs.umn.edu//6.06/ubuntu-6.06.1-desktop-i386.iso](http://ubuntu-releases.cs.umn.edu//6.06/ubuntu-6.06.1-desktop-i386.iso)

is where you get a desktop disk

---

### Post by tuxcantfly on 2006-08-21
but also, the problem may be that you didn't burn your disk properly. did you try doing "check disk for defects" on the ubuntu disk boot screen?

---

### Post by alon on 2006-08-21
10x , but desktop is what i tried...
6.06 , 6.06.1 , 5.10....
nothing worked... im currenty downloading 5.04 , hope this will do the job.

---

### Post by alon on 2006-08-21
no i didnt , but im simply burning an image... it does boot.

---

### Post by tuxcantfly on 2006-08-22
try the 6.06 desktop disk again, only burn it at a much slower speed, like 4x. 10x might be too fast for your cd burner, and it might have made your cd defective.

---

