---
title: "DVD RW not CD RW install?"
date: 2008-12-16
forum: General Help
---

### Post by tonyuk123 on 2008-12-16
Hi, i have the Ubuntu 8.04 disk burnt to a dvd.
I have previously installed it on my own desktop without problem.
However, over the weekend i tried to install it on the kids desktop pc.
It has two CD drives one being a CD ROM and the other a DVD Rom drive.
On first trying to boot from it, it just booted to windows, so i assumed the drives were in the wrong order, so i manually plugged the cable in reverse to them so the DVD Rom is the master.
Now if the bios is set to boot from CDROM, it fails, saying it is not a bootable disk.
How do i get around this? (without re burning it to a CD RW instead of DVD RW)

Tony

---

### Post by EV500B on 2008-12-16
If they are IDE drives; you've probably changed the jumpers of the DVD drive to master; If they're SATA, no problem at this state.

You can also go into the bios and configure it so that it boot first the DVD drive, but sometimes people get confused with it. 
The easiest option IMHO is for you to copy [Smart Boot Manager]("http://btmgr.sourceforge.net/download.html") to a newly formatted floppy disk and to boot from it.
This should work fine. (I think!)

PS: Some drives cannot boot at CD or DVD media at all.

---

### Post by tonyuk123 on 2008-12-20
> **EV500B said:**
> If they are IDE drives; you've probably changed the jumpers of the DVD drive to master; If they're SATA, no problem at this state.

You can also go into the bios and configure it so that it boot first the DVD drive, but sometimes people get confused with it. 
The easiest option IMHO is for you to copy [Smart Boot Manager]("http://btmgr.sourceforge.net/download.html") to a newly formatted floppy disk and to boot from it.
This should work fine. (I think!)

PS: Some drives cannot boot at CD or DVD media at all.

You were right, needed to change links on drives to make DVD drive master
Thanks
Tony

---

