---
title: "fix dual boot or virtual machine?"
date: 2009-06-21
forum: General Help
---

### Post by ahndoruuu on 2009-06-21
Okay so recently I installed Ubuntu on my Vista machine.
I was initially planning to become competent in Ubuntu and then switch over entirely, since I'm not fond of Vista, but leaving a very small Vista partition solely for gaming purposes since none of the games I play are compatible on Linux sadly and they won't run in Wine.

So, as I was in that dual-boot situation I figured "Heck, might as well get rid of Vista and install XP in its place!" 
So I did that, installed the XP over the Vista partition.
However I didn't realize that not every installation of an OS is as friendly to dual-booting as Ubuntu is until too late.

After the XP installation, I was given no choice of operating system at startup, GRUB didn't load.
Plus the XP that I installed was a custom version that had some issues so I figured I might as well just go back to Vista.
Luckily I had created recovery DVDs from the HP Recovery Partition (which I subsequently formatted and merged into my Ubuntu partition)

So I put in the recovery DVDs, it tells me it's formatting the Windows partitions and reinstalling original software and whatnot. So when that's done it asks me to restart my computer, which I do. Upon restart, GRUB still does not load, it tries to boot into Vista I'm assuming but an error comes up saying "NTLDR is missing. Press Ctrl-Alt-Del to restart". And since I had no idea how to access GRUB, I couldn't get into my Ubuntu partition either.

Now I realize this was probably a very roundabout and dumb solution, but I figured that since GRUB was installed when Ubuntu was, I'd install another very small partition of Ubuntu to regain access to GRUB, and therefore boot into my old Ubuntu installation. I did that, and it worked to gain access to the old Ubuntu.  Thinking I had accomplished what I had set out to do, I rebooted from the Gparted live CD and deleted the new, small Ubuntu partition, merging it into my old Ubuntu partition.  During next restart, GRUB began to load but then encountered an error, and the screen stayed like that.  Not knowing what to do, I booted from the Ubuntu live CD and am currently on that.

I feel pretty stupid for not really researching what I was about to do or exactly how to do it, I just plunged in and screwed things up.

So from here I figure I have two options:
1. Fix the dual-boot situation (after asking for help on this forum of course)
or
2. Format the entire disk, install a clean copy of Ubuntu taking up the entire HDD and simply run Vista in a Virtual Machine.

Which would be a more practical solution?
And if i chose the Virtual Machine method, could I install Vista using the recovery DVDs I made, or would I have to use an OEM disk?

---

### Post by merlinus on 2009-06-21
You can probably fix your dual-boot.  I would try that first, as it may be very unlikely that you could use restore disks to install windows in a VM.

Post results of:

```

sudo fdisk -l

```

---

### Post by zero777zero on 2009-06-21
for gaming, running windows through virtualbox isnt a good idea, games are usually too hardware intensive

---

### Post by ahndoruuu on 2009-06-21
@merlinus: Here are the results of "sudo fdisk -l"

"Disk /dev/sda: 360.0 GB, 360080695296 bytes
255 heads, 63 sectors/track, 43777 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1292036b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       32419   260405586    7  HPFS/NTFS
/dev/sda3           32420       43777    91233135    5  Extended
/dev/sda5           32420       43476    88815321   83  Linux
/dev/sda6           43477       43777     2417751   82  Linux swap / Solaris

Disk /dev/sdb: 1049 MB, 1049624576 bytes
2 heads, 63 sectors/track, 16270 cylinders
Units = cylinders of 126 * 512 = 64512 bytes
Disk identifier: 0x004681ce

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       16271     1025008    6  FAT16"

And I do have an OEM disk, if it develops that running through a Virtual Machine is necessary.


@zero777zero: I'm not talking about the latest and greatest games really, just Combat Arms which is a free online FPS by Nexon.

---

### Post by merlinus on 2009-06-21
Try this:

```

sudo grub
root (hd0,4)
setup (hd0)
quit

```

and restart.

---

### Post by ahndoruuu on 2009-06-21
That command worked, restored the GRUB bootloader :D

However when I try to boot into Vista I am still given a "NTLDR is missing. Press Ctrl-Alt-Del to restart"
I realize that this might not be the forum to ask about Windows issues on, but hopefully someone can offer a solution.  What's weird is that supposedly Vista doesn't even use NTLDR.

---

### Post by merlinus on 2009-06-21
supergrub may be able to help.  At least grub is back....

[http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html#Super_Grub_Disk_Quick_Help](http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html#Super_Grub_Disk_Quick_Help)

---

### Post by ahndoruuu on 2009-06-21
Yes, thank you for that. I'll try supergrub and report back with results.

---

### Post by gwyndyn on 2009-06-21
If you do go the virtualbox route, just be aware that it doesn't really have 3D graphics support, so that will limit the games you can play in it.

---

### Post by ahndoruuu on 2009-06-21
Dammit, Brasero won't burn the SuperGrub image.
It keeps failing.

>.>

---

### Post by merlinus on 2009-06-22
Your download may be corrupted.  I just burned the new version .iso using brasero, with no problems.

I also believe there is a usb stick option, if your machine can boot from it.

---

### Post by ahndoruuu on 2009-06-22
> **merlinus said:**
> Your download may be corrupted.  I just burned the new version .iso using brasero, with no problems.

I also believe there is a usb stick option, if your machine can boot from it.

I think it might be due to the fact that I'm burning it to a DVD rather than a CD but that's the only option I have.


Edit:
So it burned fine after I re-downloaded the .iso file.
Booted into it, tried just about every available option to fix the Windows but to no avail....

I think it might be possible to fix if I simply format my entire hard disk, use the Recovery Disks to install Vista, then re-install Ubuntu and repartition everything.  But the amount of time involved with that...makes me wonder if it would even be worth it.


EDIT: I did that. It works fine now. Thank you guys.

---

