---
title: "The case of the missing partition"
date: 2009-02-07
forum: General Help
---

### Post by BillOwnz on 2009-02-07
This is exactly what happened. I had Ubuntu installed (hardy) and I accidentally deleted my boot ini file thus killing my ability to boot Linux. Me and my infinite wisdom thought gparted would help by deleting my Linux partition bringing me down to just windows7 and then I could install once again. 

Of coarse that wasnt the proper way to approach this issue. But thats not why I am in trouble. Turns out gparted had an error while shrinking and expanding. My Ubuntu partition vanished taking the unused space with it! 

Here is a picture of my partitions... take note my HDD is 320gb and it only recognizes 298gb.  

[IMG]http://img5.imageshack.us/img5/3084/billtm0.jpg[/IMG]

I also get this error 

bill@bill-laptop:~$ fdisk -l
Cannot open /dev/sda


How can I get my partition back? My XP boot disk shows all 320 gb available and a reformat would fix this... but I don't want to loose and start over. 

Currently on Intrepid Ibex

---

### Post by mc4man on 2009-02-07
If it is a 320Gb drive then your xp boot disk is not reporting the actual available space.
298 available on 320 sounds about right (figure about 7gb per 100gb less than drive "size" is available

---

### Post by kayvortex on 2009-02-07
Well, according to that sceenshot, Ubuntu is there listed as /dev/sda5: is that wrong? Also, simple question, but did you run fdisk with root privileges?

---

### Post by BillOwnz on 2009-02-07
WOW im a noob... 

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       34377   276133221    7  HPFS/NTFS
/dev/sda2           34378       38913    36435420    5  Extended
/dev/sda5           34378       38721    34893148+  83  Linux
/dev/sda6           38722       38913     1542208+  82  Linux swap / Solaris


with my first linux install I had more then 298... im not sure where this space went.

---

### Post by kayvortex on 2009-02-07
The missing space sounds like it's just a mixing of naming convention. A Kilobyte is technically 1000 bytes; but, because of the binary nature of hardware storage, is also the name given for 2^10 bytes = 1024 bytes. So, two people quoting the same quantity in Gb could either be talking in powers of 10 (the correct SI expression) or 10.08.
320Gb in SI = 320 * 10^9 bytes = approx. 298Gib
where 1Gib is the correct unit for 10.08^9.
So, unless you are absolutely sure that there *did* exist unallocated space on the disk, I think your disk manufacturer has used the powers of 10 definition, and gparted has simply used the powers of 10.08 definition and there is nothing missing.

Now, fdisk is reporting the same as gparted: your Ubuntu partition is there listed as /dev/sda5, so I'm not sure what you mean when you say your Ubuntu partition has disappeared: is /dev/sda5 not supposed to be your Ubuntu partition? Also, what exactly do you mean when you say you deleted your boot ini: what file was it, exactly, that you deleted?

---

