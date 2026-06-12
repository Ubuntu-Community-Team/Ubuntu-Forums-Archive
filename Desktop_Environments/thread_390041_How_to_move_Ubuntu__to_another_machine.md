---
title: "How to move Ubuntu  to another machine?"
date: 2007-03-21
forum: Desktop Environments
---

### Post by johnd126 on 2007-03-21
I've been testing Ubuntu 6.10 on an old, pokey machine and shortly I want to move it to a speedier machine.  How can I migrate from one machine to another?  Is it possible to swap the harddrive into a completely different machine and will it discover the new hardware and boot?  

If that's not possible, are *all* my user settings saved within my home folder and can I just copy that over to a new machine after I install Ubuntu?

I'm liking Ubuntu alot but this computer is making it painful to do things!

Thanks!

---

### Post by twikletoes on 2007-03-21
You don't want to move the hard drive and try to boot because then Linux will just break.
Try to install Ubuntu on the other computer and through a network move the files and stuff over.

---

### Post by johnd126 on 2007-03-22
Yeah, I was wondering if that was what I would have to do...

I'd better set things up on a new machine before I get too many tweaks in place on this one!

It's as bad as migrating a Windows system maybe?  ;)

Thanks for your help.

---

### Post by zdude on 2007-03-22
My main machine is an AMD X2 4600 w/nvidia video and I recently cloned my hard drive and installed it into my Intel Celeron Box 2.4 gz w/nvidia card and everything came right up and was usable almost immediately. I only had to run nvidia-settings to adjust for monitor differences as well as change network settings. I am running Beryl, Vbox, Wine, etc. and everything was rocking and rolling in about 15 minutes, albeit slower. Make sure you use the generic kernel (edgy) since it works with amd/intel/smp, etc. BTW, this normally would have been a couple of days worth of work to do this on windows box.

---

### Post by johnd126 on 2007-03-22
That's awesome!  It would be sweet if I could just swap the drive into another machine.  I guess I can't lose anything by trying (after I back up  my ~ folder, of course. ;))

Thanks!

---

### Post by JoxBG on 2007-03-22
Swapping hard drive in general shouldn't break Ubuntu because the file system is intact and major device addresses shouldn't be that different. That is UNLESS the drive is being moved into a machine with a totally different configuration, like:
 - The drive becomes a secondary drive in new setup.
 - Presence of SCSI drives with priority or set as boot drives.
 - Some exoteric device that has no known device driver and takes aggressive possesion of IRQ's and DMA's.
 - Machine does not have support for existing drive configuration (eg. move a 10 GB IDE to old machine with BIOS support for only 8G max).

If it's a 'typical' IDE, at most  you might have to reconfigure some devices like graphics, sound, usb's. But I expect your machine will boot up. If it's SCSI, even better.

Jox

---

