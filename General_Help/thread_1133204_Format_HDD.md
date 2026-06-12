---
title: "Format HDD"
date: 2009-04-22
forum: General Help
---

### Post by invincibletoviruses on 2009-04-22
i would like to completely erase my hdd including my xp partition and have a clean hdd to start over. How to do this?... also can you do it with MS-DOS???

...preferably ms-dos please

-thanks

---

### Post by traderpats on 2009-04-22
Lots of options.  I'd download the disk utility from the manufacturer if you don't still have it.  They're great for real low-level formatting.

---

### Post by invincibletoviruses on 2009-04-22
i did not completely explain my problem (sorry) i used gparted to delete my xp partition but every time i try to reinstall xp it wont format the xp partition it freezes at 0% on regular format and on 20% in quick format. so i believe i may still have fragments of xp on the hdd so i want to completely wipe hdd even ubuntu. How to completely wipe hdd (with ms-dos preferably). 

-thanks

---

### Post by jsowoc on 2009-04-22
If you remove all partitions from the disk (eg. with gparted), the hard drive will be essentially "formatted". You will, of course, lose all your data that was on the partitions you removed.

If you want to do a "low-level format", you need a special disk from your hard drive manufacturer (eg. SeaTools from Seagate). You shouldn't need to ever low-level format unless you have bad sectors.

---

### Post by invincibletoviruses on 2009-04-22
speaking of low level format... what is it, and what does it do in terms of formatting?   Also...> [b]How to completely wipe hdd (with ms-dos preferably).
[/b]  

> **If you remove all partitions from the disk (eg. with gparted), the hard drive will be essentially "formatted".**
 you cannot delete the partiton that is currently active with gparted in other words you cant delete ubuntu partition while on ubuntu.

-thanks

---

### Post by sailthesea on 2009-04-22
I don't think you'll be able to format from DOS because it's almost certainly lost A Live CD with GParted or something should do the job or the low level format if you can get a utility disc It sounds like a fault in the HDD again a LiveCD will enable you to check
 Good Luck! I'm about to partition for dual boot on this machine so I hope I don't have a similar problem!

---

### Post by invincibletoviruses on 2009-04-22
> **low level format if you can get a utility disc**

> speaking of low level format... what is it, and what does it do in terms of formatting? and can i get a disk utility on ubuntu...i have a seagate barracuda here is a link to the download site:[http://www.seagate.com/www/en-us/support/download](http://www.seagate.com/www/en-us/support/download)

---

### Post by jsowoc on 2009-04-22
Low-level formatting doesn't really exist like it used to. This is re-writing where each sector is on the disk, and should be done at the factory.

For a DOS command, I suggest asking on a DOS forum.

I know you can't delete the active partition if it's mounted; you should be doing this sort of maintenance from a live CD. I suggest booting from a live Ubuntu CD. Run gparted. Delete all partitions (after backing up the data, of course). Then you should be able to do a clean Windows XP install. If not, you should get a program from your manufacturer to check the drive physically for defects.

---

### Post by Ticketoride on 2009-04-22
> **invincibletoviruses said:**
> i would like to completely erase my hdd including my xp partition and have a clean hdd to start over. How to do this?... also can you do it with MS-DOS???
Both Windows as well Linux will create the required Partitions for you. If your Install freezes, I suspect the Problem lies elsewhere.

Maybe you haven't given XP enough Disk Space to install it?

MS-DOS Fdisk will delete non-MS Partitions, but not always, and is a little limited in that respect.

> **invincibletoviruses said:**
> so i believe i may still have fragments of xp on the hdd
Doesn't matter, its overwritten anyways.

---

### Post by jsowoc on 2009-04-22
If you have a Seagate Barracuda (I do too :-) ), you can use SeaTools:

[http://www.seagate.com/www/en-us/support/downloads/seatools/](http://www.seagate.com/www/en-us/support/downloads/seatools/)

Download the "SeaTools for DOS", burn it onto a CD, and boot into it. You should be able to run a variety of hardware diagnostics on the drive. It also has a (very dangerous) "erase drive" feature.

---

### Post by invincibletoviruses on 2009-04-22
> If not, you should get a program from your manufacturer to check the drive physically for defects. where& how? i dont have xp anymore and the cd probably wont work on ubuntu...unless its a bootup disk..is it???

---

### Post by sailthesea on 2009-04-22
Quote:
How to completely wipe hdd (with ms-dos preferably).
Quote:
If you remove all partitions from the disk (eg. with gparted), the hard drive will be essentially "formatted".

 To answer your questions (I hope ):
To "completely wipe" your HDD with DOS is not really practical any more
 You are only removing the the files used to establish the discs stucture and usage when "formatting" so using a partition editor amounts to the same BUT you have do it from a LiveCD because as you have found you can't delete a  partition that you are using!
  Fire up and check out your HDD I still think you have a problem there

---

### Post by jsowoc on 2009-04-22
The "SeaTools for DOS" is a "live CD". Basically what you called "bootup disk". You don't need to have anything installed anywhere to run it, but you do need an OS to burn the .iso file onto a CD.

I recall there being a DOS command "zerodisk", which writes zeros to all writeable sectors on a hard drive, but the SeaTools is probably a safer/better option (it also runs diagnostics).

---

### Post by invincibletoviruses on 2009-04-22
> It also has a (very dangerous) "erase drive" feature.
is that what i need to erase my hdd completely including ubuntu and starting ultimately over like when i first custom built my pc??? thats all i want to do start over.... just don't know how

---

### Post by theozzlives on 2009-04-22
As an old DOS user, I can safely say DOS is a thing of the past :(. If you have a Win98SE CD you can run fdisk and format in FAT32.

---

### Post by invincibletoviruses on 2009-04-22
nvm opps

---

### Post by jsowoc on 2009-04-22
From my experience, removing the partition with Windows using Gparted should give Windows a "fresh start", and you should have been able to install Windows in the free space.

Because this does not work, we suspect your hard drive may be faulty. Seagate makes a program "SeaTools" (I posted this above already) that can be burned onto a CD (or put on a floppy). Your computer can be told to start from said CD/floppy, and you can then run diagnostics on the hard drive.

Download SeaTools from here:
[http://www.seagate.com/www/en-us/support/downloads/seatools/seatooldreg](http://www.seagate.com/www/en-us/support/downloads/seatools/seatooldreg)

If the (non-destructive) diagnostics do not reveal errors, but you still cannot install, SeaTools will let you do a "full erase". This should be considered a last resort.

Download SeaTools, put it onto a CD/floppy, and try the diagnostics.

---

### Post by invincibletoviruses on 2009-04-22
very well then i will do the diagnostic and see the result but if i just want a fresh hdd can i do full erase without risk???
also is the dos utility an advanced utility with commands or is it more simple like clicking stuff or selecting options with the arrow keys??? (i understand most terminology just want to know if i need to memorize any commands???)

thank you very much!!!!

---

### Post by invincibletoviruses on 2009-04-23
I did diagnostic for my HDD no bad sectors were found. I decided to do full erase with the Seatools dos utility. It freezes up at 64%.  What’s wrong the HDD is ok according to the Long Diagnostics test but it won’t format????

---

### Post by invincibletoviruses on 2009-04-23
!!!SOLVED!!! i did the format over and it worked!!!!!!!!!:guitar:

---

### Post by Ticketoride on 2009-04-26
> **sailthesea said:**
> You are only removing the the files used to establish the discs stucture and usage when "formatting" so using a partition editor amounts to the same BUT you have do it from a LiveCD because as you have found you can't delete a  partition that you are using!
There are no Files, just an MBR Table Entry on Sector 0 of the Disk. No Files are deleted formatting a Disk, and can be salvaged by Data Recovery Applications on that Basis, be it Linux, Windows and what not.

FDISK may not recognize the Entries in the first Sector nor be able edit it even after **%:\>fdisk /mbr**

[HDD: Low Level Format Tool]("http://hddguru.com/content/en/software/2006.04.12-HDD-Low-Level-Format-Tool/")

When they say "Erase" ... they mean "Overwritten".

---

