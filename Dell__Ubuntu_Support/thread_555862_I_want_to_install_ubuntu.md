---
title: "I want to install ubuntu"
date: 2007-09-20
forum: Dell  Ubuntu Support
---

### Post by ticknubbs on 2007-09-20
I just got my live cd of ubuntu and i dont see anywhere on it that says install and then also when i try to boot from the cd it never works and goes to the secondary device(c drive) and starts windows xp. I would also like to keep xp on there so i can run either os when desired...is this possible?

---

### Post by dje on 2007-09-20
At immediate boot up go into your bios and move your cd/dvd drive to the top of the boot order and then reboot with the ubuntu disc in your drive. Then select start/install ubuntu. HTH

---

### Post by ticknubbs on 2007-09-20
i have done that already and something appears on the screen so fast then it goes to the secondary device and boots from the hard drive. Any Ideas?

---

### Post by dje on 2007-09-20
Did you burn the .iso as an image? if not reburn it as an image.

EDIT: there should be lots of files and folders on the cd, if you only see one .iso you need to reburn as an image

---

### Post by ticknubbs on 2007-09-20
i did not burn anything...the cd was mailed to me

---

### Post by dje on 2007-09-20
sorry then, i dont have any more ideas :confused:

---

### Post by Keiran230 on 2007-09-20
> **ticknubbs said:**
> I just got my live cd of ubuntu and i dont see anywhere on it that says install and then also when i try to boot from the cd it never works and goes to the secondary device(c drive) and starts windows xp. I would also like to keep xp on there so i can run either os when desired...is this possible?

It is possible to have both Windows XP and Ubuntu installed on one hard drive if you partition it correctly, but I have no idea why it wouldn't boot from CD when you tell it to. The only error I've ever had booting from CD was when it brought me to a black screen with random white text nonsense on it.

---

### Post by rsambuca on 2007-09-20
Check your pc manufacturer's website for instructions on how to enter the bios.  All computers have a means of accessing the bios at bootup.  You will have to enter it and set the CD drive as the first boot device.

The methods of entering the bios differ from manufacturer to manufacturer.  Some it is Esc, some F1, F12, etc.  Until you do that, you can not use the CD.

---

### Post by Monkey_Tales on 2007-09-21
Indeed, first startup your pc with F12 or F5 and select to startup from cd
When it works and ubuntu has started up, there is an icon on the desktop with 'install' for the Ubuntu install and go from there.
You have to make 3 partitions. 2xpartitions EXT3 and 1x SWAP
1 EXT3 for "/" directory (2GB or more)
1 EXT3 for "/home" directory (2GB or more)
1 SWAP for "swapdrive" (1GB)
This all comes up in the install procedure.
:popcorn:

---

### Post by trebach on 2007-09-22
On a Dell, before the black and blue DELL screen disappears, press F12, select your CD/DVD drive and hit ENTER.

---

### Post by deserthowler on 2007-09-22
On my Dell OptiPlex GX110 I couldn't get either the Live or Alternate 7.04 CD to boot.  Live is from Ubuntu and Alternate is unpacked iso.  Never saw anything but the blank screen with the cursor flashing.  ](*,)

I found a book, I think "Ubuntu for Dummies", at the public library which included 6.10 and that installed.  I installed 6.06 and Debian Etch with no problems.  I have problems running Live CDs from several distros including Knoppix, Freespire, and PCLinuxOS on that machine but an older version of gparted works find.

I have no clues.  As Chief Dan George said in "Little Big Man", "Sometimes it works.  Sometimes it doesn't."

Earl

---

