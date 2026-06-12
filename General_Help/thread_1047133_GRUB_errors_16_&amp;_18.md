---
title: "GRUB errors 16 &amp; 18"
date: 2009-01-22
forum: General Help
---

### Post by Colin@oxford on 2009-01-22
Once in a while (possibly every 20 reboots) recently, my computer has started generating GRUB errors on boot.  Firstly:

```
Error 16: inconsistent filesystem structure 
```

and, if I press any key to get back to the GRUB menu and try again:

```
Error 18: Selected cylinder exceeds maximum specified by BIOS
```

Every time if I use "c" and then "reboot" it has the started OK.

Should I be worried?  What action is recommended?

The PC is about 8 months old.  The /boot directory is in its own partition.

---

### Post by azmo35 on 2009-01-22
Hi, for the error 16 you can use gparted live cd boot that and right-click on the filesystem you need to check and select 'check' from the right-click menu. That will fix a lot of filesystem problems.For error 18 the "hd" have limitations so you pass that limitations reduce the size of the linux partition,or check your computer's BIOS date and settings in case your BIOS can be updated instead,i hope this help.

---

### Post by Colin@oxford on 2009-01-22
When booting Ubuntu the file systems are checked on a regular basis.  Is this the same action as what gparted would do?  The puzzling thing to me is that the problems are intermittent.  Error 16 always occurs first and error 18 second - even when pressing "c" after the first error, 18 comes up just before the grub prompt.

---

### Post by azmo35 on 2009-01-22
Hi,the action that gparted will do is diferent and if you don't know hard disc have limitations max 137gb so the error 18 is because of that, is gparted solve the error 16 you end up only with error 18 and maybe if you resize the two partitions a bit maybe this solve the problem,i hope this help.

Sorry,if you have a desktop and change something inside check your SATA drive cables.

---

### Post by ronrafajko on 2010-01-08
I too am getting the errors 16 then 18, on my Ubuntu 9.10 dual boot laptop.  

Mine appeared after files were lost on my Windows partition and scandisk was run by Windows.  There were a ton of changes made by scandisk, and I suspect my laptop HDD is starting to fail (new bad sectors).  I thought scandisk may have trashed the GRUB install, so I followed the "How to restore Grub from a live Ubuntu cd" to no avail.

I can boot to a live cd and mount the drives okay, so the error 18 does not make sense.  I do have a problem on my root partition.  One directory that should have around 10GB of data is showing as empty now.  If I did not need that data I would have just reinstalled Ubuntu on it.

I tried the gparted recommendation above (clicking on 'check') on the Windows NTFS partition, but got the error, "An error occurred while applying the operation".  The details reveal bad sectors.  I will try the Trinity Rescue Kit and see if I can get the boot working again.

Any other things I should try?  

THANKS!

---

### Post by Colin@oxford on 2010-01-08
I think that you have a failing disk.

My computer was eventually diagnosed as having both a disk fault and then a motherboard fault. The disk was replaced first (the retailer said that the disk was beyond recovery) but the machine soon developed the similar problems, including freezing at random). Eventually the whole machine was replaced (with the memory, disk etc. transferred over.

That does not, of course, solve your problem,  However, if your machine is new then you should get it repaired/replaced under guarantee.  You do take backups, don't you?

---

