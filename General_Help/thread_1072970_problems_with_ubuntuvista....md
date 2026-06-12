---
title: "problems with ubuntu/vista..."
date: 2009-02-17
forum: General Help
---

### Post by hexagondun on 2009-02-17
i have a dual boot with main running vista secondary running ubuntu.  Im trying to intall xp over my vista hard drive.  when i put the disk in it loads all the necessary files then tells me it cant see either of my hard drives.  in vista my hard drive can be recognized, in ubuntu it cant mount SOMETIMES, but neither of them can be seen by the xp setup .exe 

what could possibly be the problem here?  also is there a way to view my ubuntu drive thru vista so if worst comes to worst i can reformat that one, install xp on it then install ubuntu on my primary.  thanks guys!

---

### Post by x33a on 2009-02-17
you can delete the vista partition from ubuntu using gparted. then install xp over that partition. you'll have to fix the bootloader after that, though.

---

### Post by hexagondun on 2009-02-17
its not a partition on the same hdd its a seperate hard drive.  
also, i dont know much about ubuntu, what's bootloader and what will i need to do to fix it?

---

### Post by x33a on 2009-02-17
when you boot up your computer, you get an option to select an os to boot from a list. that is done through a bootloader.

[http://en.wikipedia.org/wiki/Booting](http://en.wikipedia.org/wiki/Booting)

edit: since, you have ubuntu already installed you don't need that installation guide.

just boot into ubuntu, press alt+f2, open gparted. format the vista partition.

then use the xp disc to install xp over the vista partition.

---

### Post by hexagondun on 2009-02-17
will this destroy my bootloader?

---

### Post by my window broke on 2009-02-17
is it an external hard drive or a secondary internal one?

and yeah, it shouldn't destroy the bootloader but it will not have an up to date reference to the new XP partition, and thus not be able to boot from it. Remaking a new grub loader is actually not that hard.

---

### Post by hexagondun on 2009-02-17
secondary internal hdd

---

### Post by my window broke on 2009-02-17
> Reinstalling or fixing Grub after error 21:

   1. Boot into the original Linux system with the external hard drive still installed (or you can boot from a Live Ubuntu CD).
   2. Open up a terminal and type sudo su
   3. Type fdisk -l and locate your Linux boot partition from the list Example: sda1 or hda1
   4. Type grub-install /dev/sdx or grub-install /dev/hdx to reinstall or repair Grub!
   5. Reboot and test!

      Notes: x represents the drive letter a, b, c, d etc. Replace with your actual drive letter.

      sdx= SATA, SCSI or USB devices hdx= IDE devices

that is what I did to fix my grub after I got an error 21 installing to an external hard drive


Also, is your secondary internal HDD a Primary or Secondary?
Might run into problems on a secondary

---

### Post by hexagondun on 2009-02-17
im logged in as root and still it wont let me delete partitions in gParted.  the windows hard drive is grayed out, and my ubuntu drive isnt, but the "delete" is.  this help is greatly appreciated, im lost:(

---

### Post by hexagondun on 2009-02-17
i think my secondary internal hardrive (one with ubuntu) is my secondary drive.  it says my windows drive is unallocated and my ubuntu one is ext3 also, can ubuntu recognize ntfs or fat?  im gettin nervous here

---

### Post by hexagondun on 2009-02-18
well, i did something, that's for sure.  just tried to boot windows and it says no such partition exists.  this could be good or real bad.

---

