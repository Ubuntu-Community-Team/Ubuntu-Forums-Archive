---
title: "Deleting Windows without affecting my Ubuntu install..."
date: 2006-08-16
forum: Desktop Environments
---

### Post by BayGuy27 on 2006-08-16
Hello all,

I am looking to delete Windows without "messing up" my ability to boot into Ubuntu. I have the grub boot loader installed. When I have reinstalled Ubuntu, with Windows XP installed on another partition, I booted into my Windows XP CD, into recovery console, ran 'chkdsk /r' to rewrite my windows boot file so Grub is not active, look for Ubuntu. I then formatted the ubuntu partitions using bootable Partition Magic and reinstalled.

I am not sure how to tackle removing Windows, and then probably performing a clean install of Windows down the road, without affecting boot access to Ubuntu. Any help would be appreciated! Thanks,

Dave

---

### Post by hecato on 2006-08-16
A guess.. if you have boot floppy unit, then if you lose your boot manager...

then in synaptic search for grub-disk (the name)

> 
**GRUB bootable disk image**
This package contains a GRUB rescue disk. It consists of a bootable
1.44 floppy image you can use to grab a rescue disk or be run in an
i386 emulator, like Bochs.



I know you can reinstall the boot manager on HD, but dont know the command exactly.

At less in taht way (see wich files are installed and the commands if there are in the propierties of the package) you will be able to boot fom floppy disck, try it... and see if there is look in boting from floppy. before you delete your Windows partition (alo see if partition numbers change when you delete it in the future).




By the way, dont know if in the liveCD is there a tool (should be) for reinstall the bootmanager grub.

---

### Post by orb9220 on 2006-08-16
Well of course when you install xp down the road it will wipe the mbr. So  you need to restore the grub.

This might help  [http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub)

---

### Post by OrganicPanda on 2006-08-16
I know it's not the same but I'm looking to ghost my ubuntu (because everything is set up the way I like it), delete everything else AKA windows, format and then restore my ubuntu but I'm wondering if this will land me in some trouble, I don't know exactly how ghosting a drive works or if it will work for linux atall but my HDD is a mess and really needs to be wiped clean, I'm wondering will I need to restore my grub after such an operation?

---

### Post by orb9220 on 2006-08-16
Well there are a couple of ways. Ghosting means using a program to make a backup of the partition usally to a usb drive or DVD disc which you can boot from and it will write the partition track by track to the target partition.

Using backup commands such as rsync or tar you will be doing a file by file copy with option of compression to a location then the resulting file can be moved to another media like burning to dvd or moving to a usb drive.

[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html) is one example also just search forums for tar and rsync for how to use.  Caution:rysnc cannot backup to fat32

Hope this helped a bit.

---

### Post by OrganicPanda on 2006-08-16
Hmm that sounds quite interesting, I will definetly check that out, Cheers

---

