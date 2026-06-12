---
title: "GRUB Error 15 (dual boot with XP)"
date: 2006-03-27
forum: Desktop Environments
---

### Post by chriszanf on 2006-03-27
Hello all,

I have spent pretty much most of my day trying to install ubuntu with no success at all.

I have my machine set up to dual boot with XP but Im trying to keep the OS's seperate by not installing GRUB to the MBR on my hda but I keep repeatedly getting an "Error 15".

I have run through the install procedure correctly (to teh best of my knowledge) and have repeatedly checked on threads here if I am installing GRUB correctly.

My HDD format is as follows:

hda 160Gb
#1    25Gb    XP Boot
#2    60Gb    NTFS partition [logical]
#3    66Gb    NTFS partition [logical]

hdb  80Gb
#1    23Gb    Primary  ext3  /
#4    250Mb  Primary  ext3  /boot
#5    1.1Gb   Logical  swap /swap
#2    55Gb    Primary  [empty - unformatted]

I have run through the install process and when it gets to installing GRUB, I choose to place it on hdb4 and yet it keeps returning the error 15.

I tried running through an install as "linux acpi=off" and GRUB installed and booted to the choice screen but failed to see ubuntu installation to finish the install process.

Ive been trying this since about 5pm (its now 11pm) and Ive pretty much lost all hope of getting ubuntu installed without GRUB being on the MBR. 

Can anyone offer any advice or tips to get this to work?

Many thanks

---

### Post by gazj on 2006-03-27
I know this isn't a very good work around, but it is one that i used to use when i dual booted

change your bios settings so that your your second hard drive is the first one that is booted, it should then be known as hda

Install ubuntu as a single operating system to hda

after install you can switch between os by chainging your boot device in your bios, which is a start, i know its not perfect

then if you boot your ubuntu, you can edit your grub so that it can start up windows on hdb.

the good thing is if you ever remove your ubuntu drive, you can still boot into windows as you always did, by just setting your boot device back to your first hard drive (or if you mess up grub)

In fact when i was doing it, i disconnected my windows drive, until i finished the ubuntu installation just to be sure, i would recommend you do this to, that way you know your going to be safe.

If by some chance you do mess you windows mbr, you can replace it by inserting the xp cd, and starting recovery mode, and using the command fixmbr

i hope this helps, its a bit far fetched and if i havent made it very clear have a moan at me, and ill try to make more sense

Good luck

---

### Post by chriszanf on 2006-03-27
Gaz,

This is exactly the thing I have been trying to do. I was trying ot set it up that I went into BIOS each time so that if I removed the drive or either install failed, it wouldnt affect the other.

I failed to realise [like I would ;)] that when I was changing the boot order in the BIOS that the hdd lettering was changing.

Thank you for taking the time to reply and help out!!

---

### Post by gazj on 2006-03-27
no problem (remove that windows drive!!! it makes sense)

---

