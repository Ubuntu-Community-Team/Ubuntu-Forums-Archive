---
title: "No Drives on 8.94 Desktop"
date: 2008-04-27
forum: Desktop Environments
---

### Post by oldefoxx on 2008-04-27
I had a problem under 7.10, which is that my IDE drives were tagges as SCSI devices with removable media, so that the drives actually showed up under the /media folder, but at least they were there, and appeared on the Desktop.

Now under 8.04, they don't show up either place.  I have to use Places.Removable Media to locate the drives, mount them, at which point they appear on the desktop.  I don't like this.  And it is playing havoc with my ability to access the drives from within my VirtualBox environment as shared folders.

Anybody got a fix for this?  I've reported it as a bug, and as you can see, the bug is just getting more extreme all the time.  IDE drives are not SCSI devices, they do not classify as removable media, and they should not have to be mounted manually to be accessable.

---

### Post by scragar on 2008-04-27
things in /media get desktop icons, things in /mnt don't, which is why /media is defaulted :P

add the line to /etc/fstab (opening gedit like so:```
sudo gedit /etc/fstab
```) like so,  where the information can all be found via the ```
mount
``` command:
```
/dev/sd**b1**	/media/**MOUNTPOINT**     auto    defaults        0       2
```
auto defaults and 0, 2 are best unless you know what your doing, if you don't then please don't edit that part of the line. replace b1 with the relevant part you need.

---

### Post by oldefoxx on 2009-05-20
Thanks for taking the time to answer.  I had a problem adjusting away from the manner in which things worked in the earlier versions, where the drives immediately showed up as icons on the desktop.  So it takes a few steps longer now to go under Places/Removable Media and locate the drive in question, then click on it and have it mounted and show up on the desktop?  Big deal.  That is probably more consistent with what most people want anyway.

Although it is a bit of a stretch to think of an internal hard drive that is always present as being Removable Media.  Not without a screwdriver and partial disassembly of your PC is it anything approaching removable, and even then you might need specific model instructions as to how to get the drive cage out where you can remove the drive.  Oh yeah, a good follow though is for the vendor or OEM to provide a good reference about that model PC to go to online.  That's one of the reasons I prefer HP PCs, they do a really good job in this respect.  Just visit [www.hp.com](www.hp.com).

---

