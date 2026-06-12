---
title: "[SOLVED] Dual Boot Ubuntu and XP on seperate drives"
date: 2007-11-14
forum: Desktop Environments
---

### Post by Akt on 2007-11-14
Hi everyone!  Lovely day, been using Ubuntu for quite a while and love it!!!!  I've decided to install Windows XP (work requires it) on a separate hard drive as a slave to the drive I have Gutsy installed on.  My BIOS won't allow me to choose which hard drive to boot to so, I thought if I modified my menu.lst and added this line:

title		Windows XP
root		(hd1,0)
makeactive
chainloader 	+1	

...I would be able to see Windows in the boot menu.  Well, I do, but if I choose it, I just get the message, "Starting Up..." and it hangs.  I can boot into either O/S if I unplug the other drive from the IDE cable, but I'm tired of opening the case every time I want to switch back.  Any ideas?

---

### Post by baphomet420 on 2007-11-14
if you do not mind reinstalling ubuntu, you can do this...

hook up booth drives...  reinstall by booting to live cd, and reinstalling over that hard drive...  if windows vista is hooked up and your bios does in fact see the hard drive, then ubuntu should see it on install and automatically install the grub boot menu loader...  

there may be ways of installing this without reinstalling ubuntu, but its out of my area of expertise :)

---

### Post by baphomet420 on 2007-11-14
or, if you have enough ram and cpu to run booth at the same time, you can install a really nifty program called virtualbox...
this will let you run xp from within ubuntu....

---

### Post by Akt on 2007-11-14
Thanks for the quick reply!  While I do have enough RAM to run Virtualbox, I have to have Windows XP running alone for my job.  I've reinstalled both several times but at this point I have them both configured the way I need them to run and I'd rather not have to reinstall again.

I'm sure I"m just missing a small configuration step in the grub loader, but alas, I'm still a newbie. :)

---

### Post by bingoUV on 2007-11-14
Please give the output of the following command
```

sudo fdisk -l

```

---

### Post by Akt on 2007-11-14
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60424   485355748+  83  Linux
/dev/sda2           60425       60801     3028252+   5  Extended
/dev/sda5           60425       60801     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
240 heads, 63 sectors/track, 10333 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       10332    78109888+   7  HPFS/NTFS

---

### Post by johoe on 2007-11-14
maybe you can try:

map: map TO_DRIVE FROM_DRIVE
    Map the drive FROM_DRIVE to the drive TO_DRIVE. This is necessary
    when you chain-load some operating systems, such as DOS, if such
    an OS resides at a non-first drive.


title Windows XP

map (hd0,0) (hd1,0)

root (hd0,0)
makeactive
chainloader +1 

or the other way round:) I had this working for years...

joho

---

### Post by njparton on 2007-11-14
I tried this about a year ago and eventually gave up.

I now let my system boot automatically into ubuntu and if I want to use windows I use the boot loader built into most modern bioses to select a different hard drive to boot.

Try pressing the esc key during POST to get to a list of bootable hard and optical drives.

---

### Post by Akt on 2007-11-14
Thank you everyone that replied.  The solution that Johoe supplied was the code I needed.  Awesome teamwork, long live the Linux community!

---

