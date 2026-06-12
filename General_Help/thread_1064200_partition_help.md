---
title: "partition help"
date: 2009-02-08
forum: General Help
---

### Post by trikster_x on 2009-02-08
I want to resize my Ubuntu partition to free up space to create a /home partition. When GParted gets to shrink filesystem, it fails telling me to run 'e2fsck -f /dev/sda3' first. The problem is Gparted does this automatically before it attempts to shrink the partition, and immediately after the shrink fails. I have even tried to manually run the command through a terminal, but still get the same error. There are no errors found when the e2fsck completes, so I don't see why GParted returns this error. I don't have any screenshots since the computer I am attempting this on a computer I can't connect to the internet in liveCD mode.

---

### Post by utnubuuser on 2009-02-08
I've had gParted show the same messaghe at some point or another.  If I remember corectly, I ended up having to use a different version of the gParted iso.

---

### Post by trikster_x on 2009-02-08
The only problem with that is that the computer I am having a problem with is an Aspire One so I don't have a disc drive to load an .iso from, sorry I didn't mention that sooner.  Is there anyone that can help me to get this going off the liveCD program that I have on my usb stick?

---

### Post by x33a on 2009-02-08
first make sure that the fs you are trying to shrink doesn't have files scattered all over (enough empty space), then try the format.

as for flash-drive gparted:

[http://gparted.sourceforge.net/liveusb.php](http://gparted.sourceforge.net/liveusb.php)

---

### Post by trikster_x on 2009-02-09
I am using ext3 FS in my Ubuntu partition, and it has over 100 GB free and less than 1% of the used space is fragmented.  Why wouldn't the version of GParted that comes with the Hardy liveCD image work?  I used it to partition my drive before I installed Ubuntu, so shouldn't it be fine for partitioning now?

---

### Post by utnubuuser on 2009-02-09
Maybe there's a file type on the drive that's giving that version of gParted a hissy-fit.

---

### Post by Ericyzfr1 on 2009-02-09
Have you tried to use Gparted on a live cd? I think the version is 0.4.1-2

---

### Post by trikster_x on 2009-02-09
The new version of GParted worked =D  Thanks to everyone for the help.

---

