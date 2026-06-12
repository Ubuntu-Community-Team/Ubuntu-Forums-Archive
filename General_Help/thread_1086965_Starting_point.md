---
title: "Starting point"
date: 2009-03-04
forum: General Help
---

### Post by fa355115 on 2009-03-04
Hi there !

I actually have a laptop HP Pavilion with Windows vista (ntfs), 2 hdd of 250 gb and a hidden system partition of 5 gb (for restauring the system)

I'd like to start with ubuntu, but I have these general questions before I start :

- How can I install ubuntu in dual boot with vista - how do I need to re-partition vista to have ubuntu working ?

- the best would be that I can access my vista documents, pictures, movies, and so fro, ubuntu - is this possible (some of those documents are on the C drive, and other on the D drive

- I have read ubuntu could only read my ntfs files, and not write on them - does that mean I could open a doc file, but not modify and save it under ubuntu ?

Many thanks !

---

### Post by Titan8990 on 2009-03-04
Dual booting instructions: [https://help.ubuntu.com/community/WindowsDualBootHowTo](https://help.ubuntu.com/community/WindowsDualBootHowTo)


Linux has full read/write support for NTFS drives so you won't have a problem working with your Windows files in Linux.

---

### Post by bigb2007 on 2009-03-04
Latest 8.10 NTFS read/write support : 
[http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Mounting_NTFS_Partitions_.28with_read.2Fwrite_privileges.29](http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Mounting_NTFS_Partitions_.28with_read.2Fwrite_privileges.29)

---

### Post by chriskin on 2009-03-04
ubuntu can write on ntfs just as good as windows can - a package might be needed to get installed but it is just some clicks
ubuntu can also access any disk that is in or plugged to the computer

if you install ubuntu, you will get grub with it
grub is a menu that is shown when computer starts and lets you choose your os
probably you will have to shrink the vista partition via gparted live cd or install ubuntu in another partition


(writing 5 lines makes other post theirs before you :P hehe)

---

### Post by fa355115 on 2009-03-05
ok ... Concerning the installation, I still need to read the provided instructions; but what would you do at my place ?

I have 2 hdd on my laptop ( 2 x 250 gb ntfs).

Disk 1 : C drive : 2 partitions : Vista + 5 gb reserverd for "system partition HP recovery)

Disk 2 : Data only.

When I have to reinstall my PC, Imn just using the HP recovery tool which would only reinstall vista on the C drive, and keep my data safe on the D drvice.

So where should I install ubuntu for the dual boot ?
Is it safer on the D drive (so that I can remove it without touching anything to vista ?)

Thank you !

---

### Post by chriskin on 2009-03-05
in case that you DO know that windows' system recovery will not hurt the linux installation, it might be better to have both OSes in the same drive. there is no real difference , at least none that i know of, but keeping the 250gb data-only drive as full 250gb sounds better to me.

it seems it is up to you though

edit : having it in "C" (as windows calls it) and then removing it (that i really think is impossible, i can't think why you would want to do that :P) will not hurt vista, it will just let an empty partition that you can format to whatever you want or merge it with vista's

---

### Post by fa355115 on 2009-03-05
I heard the MBR would be "corrupted" in vista when removing the ubuntu, letting in this MBR some code about the - removed - ubuntu ?

---

### Post by chriskin on 2009-03-05
i have no idea , let's wait for someone else to answer that

---

