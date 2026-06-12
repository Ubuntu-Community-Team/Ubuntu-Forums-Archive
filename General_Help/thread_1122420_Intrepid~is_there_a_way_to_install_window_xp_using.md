---
title: "Intrepid~is there a way to install window xp using recovery disk in ubuntu terminal?"
date: 2009-04-11
forum: General Help
---

### Post by KEE on 2009-04-11
I dont mind reinstalling windowxp. I am sure, if its is possible, you must copy all the disks into a directory. anyway, if it is possible please say so. reason why I have to reinstall is because I had the "missing system32/hal.dll" on start up. I fixed the boot.ini but I just have recovery cd's from IBM, never got the chkdsk.exe to fix the system32 files. need help in directions on how to launch the recovery disk in terminal. i can do it in dos and i have [http://gd.tuwien.ac.at/linuxcommand.org/lts0050.php#mv](http://gd.tuwien.ac.at/linuxcommand.org/lts0050.php#mv) but alot of those commands dont work or i am not able to get them to work. Oh and the drive is partition with this linux. Please help

---

### Post by lavinog on 2009-04-11
> **KEE said:**
> I dont mind reinstalling windowxp. I am sure, if its is possible, you must copy all the disks into a directory. anyway, if it is possible please say so. reason why I have to reinstall is because I had the "missing system32/hal.dll" on start up. I fixed the boot.ini but I just have recovery cd's from IBM, never got the chkdsk.exe to fix the system32 files. need help in directions on how to launch the recovery disk in terminal. i can do it in dos and i have [http://gd.tuwien.ac.at/linuxcommand.org/lts0050.php#mv](http://gd.tuwien.ac.at/linuxcommand.org/lts0050.php#mv) but alot of those commands dont work or i am not able to get them to work. Oh and the drive is partition with this linux. Please help
Many times the recovery partition is accessable by pressing a Function key during the boot logo.
Usually there will be something that says "press f1 for recovery"

---

### Post by KEE on 2009-04-11
> **lavinog said:**
> Many times the recovery partition is accessable by pressing a Function key during the boot logo.
Usually there will be something that says "press f1 for recovery"

but wont this rewrite over ubuntu? they both are partition on the same drive

---

### Post by KEE on 2009-04-11
?

---

### Post by KEE on 2009-04-11
still need help ! maybe someone could confirm that it wont rewrite over evrything on the drive and just be able to recover that side with a broken windows

---

### Post by lavinog on 2009-04-11
It is likely that it will over write your ubuntu partition. Also my compaq laptop would attempt to remove grub just by loading the recovery partition (even if I don't do anything)
I would recomend backing up your ubuntu partition.
After you get windows installed back on, Image the partition so next time you just have to load that image back
[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

Also be aware that the recovery partitions don't always work. I had an e-machine that would fail mid-install. It is nice to have the discs available.

---

### Post by KEE on 2009-04-11
> **lavinog said:**
> It is likely that it will over write your ubuntu partition. Also my compaq laptop would attempt to remove grub just by loading the recovery partition (even if I don't do anything)
I would recomend backing up your ubuntu partition.
After you get windows installed back on, Image the partition so next time you just have to load that image back
[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

Also be aware that the recovery partitions don't always work. I had an e-machine that would fail mid-install. It is nice to have the discs available.

hmm i couldn't find anything for a 32 bit i386 desktop

---

### Post by KEE on 2009-04-11
ok i think i found "Sysresccd-manual-en Burning a DVD RW from SystemRescueCd by mounting it" 

[http://www.sysresccd.org/Sysresccd-manual-en_Burning_a_DVD_RW_from_SystemRescueCd_by_mounting_it](http://www.sysresccd.org/Sysresccd-manual-en_Burning_a_DVD_RW_from_SystemRescueCd_by_mounting_it) 

so i just follow the steps and it might work?

---

### Post by KEE on 2009-04-12
hmm no luck =( I all so found this [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087) Ive been looking in the threads and seeing if there is a reply that resembles my situation  and I couldn't find one =( any help is much appreciated please and thank you

---

### Post by lavinog on 2009-04-12
Do you have an external hd?
how much space do you need for your backup?
If you are limited on space you could focus on backing up your home folder and just reinstall ubuntu after you recover windows

---

