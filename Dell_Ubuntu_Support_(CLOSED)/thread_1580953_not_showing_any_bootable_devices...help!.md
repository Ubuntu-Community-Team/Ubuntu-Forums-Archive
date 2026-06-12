---
title: "not showing any bootable devices...help!"
date: 2010-09-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by tambourineman86 on 2010-09-24
Hi guys, I'm new here.  Running Ubuntu 10.4 on desktop, love it.  Thought I would put it on my laptop.  I have an XPS M1210 that a "friend" messed up during a botched reinstall of windows.  I already was getting a "no bootable devices" error message when trying to boot.  On top of that, the keyboard does not work (except for apparently the "n" and the down arrow) so I can't get into bios.

The reason I post is, on a whim, I decided to plug the usb drive that has ubuntu 10.4 on it into this broken laptop to see if it would work, and lo and behold, I was able to run the ubuntu trial!!!  Oh joy!  But, unfortunately, when I went to install it, 1. keyboard still didn't work and 2. ubuntu does not recognize any bootable device other than the external that I connected to run ubuntu.  I even opened gParted and it did not recognize the lappy's internal hd.  There seems to be no way to undo the damage that my retarded friend wreaked.  Or is there?  I'm really hoping there's some way to fix this, find a way to make ubuntu recognize the hard drive and reformat it, or is it the motherboard?

Hopefully someone with more knowledge can help me out, but I understand if the lappy is completely bricked...Thanks in advance for any suggestions and help.  And of course, let me know if any of the helpful parties need more troubleshooting information.

---

### Post by grahammechanical on 2010-09-24
I do not know about laptops but desktop motherboards have a jumper setting that allows you the re-set the BIOS back to the factory default settings. I have never tried this myself but may be you need to do something like that. Do you have the laptop instruction booklet? Does that help? As regards the hard disc I think the MBR (Master Boot Record) has been messed up. Look for some way to run a terminal and issue some kind of command to restore the MBR. This is possible. It is the way convert a duel boot HD back to Windows only. GRUB is put in the MBR. So, converting it back to the way it was effectively makes the Linux installation invisible. Do not be so quick to write off the laptop as bricked. 

Regards.

---

### Post by tambourineman86 on 2010-09-24
thanks for the quick reply.  Do you know where I could find out where this motherboard reset is?  I've partly taken apart the lappy and I can't find it.  Also, since I posted, I messed the computer up inadvertently by thinking I could possibly install the os onto an 4 gig class 6 card.  Install went fine but when it rebooted, I get a grub error.  Funny you should bring up that term.  I don't think the motherboard knows how to communicate with an sdcard as its primary partition.  Anyways, i think this reset is the holy grail that will fix it all.  I just need some help finding it.  Google sucks at finding things like this.

---

