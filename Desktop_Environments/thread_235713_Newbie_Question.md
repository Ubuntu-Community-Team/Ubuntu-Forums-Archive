---
title: "Newbie Question"
date: 2006-08-13
forum: Desktop Environments
---

### Post by DiskEdge on 2006-08-13
I am able to install and run Unbuntu v. 6.06 LTS on my desktop machine but only in Graphics Safe Mode.  In this mode all works fine but if I try to let the normal install proceed forward I get error messages that state the X Server is not set up correctly.  More specifically, it states that:

1.) No devices detected.

2.)Fatal Server Error; No Screens Found.

All this mention of the word "Server"...have I downloaded the wrong version for personal desktop use?  The download page doesn't seem to designate between the two as far as the download links are concerned.  Any help would be appreciated.

I run an ASUS A8N-SLI Deluxe MB, Opteron 165 dual core processor, 1Gb RAM and and ATI Radeon X800 GTO video card. Thanks.

---

### Post by bodyguard on 2006-08-13
The word Server means X Server - a video card driver and screening subsystem
I think that your video card is not recognized properly

---

### Post by bodyguard on 2006-08-13
I found you some help in Wiki:
Problem: No monitor found-install stops

You will need to download the 'alternate' version iso and install in text mode. when it comes to configuring xserver-xorg options, you will need to know for your model:-

horizontal and vertical sync / display resolutions / hz it can run at

or some intes (intel) and ati cards require driver

eg Card: Sapphire ATI Radeon x800 GTO PCI-E

In a terminal type

sudo apt-get install xorg-driver-fglrx sudo aticonfig --initial sudo aticonfig --overlay-type=Xv

I hope it helps but its an ugly workaround

---

### Post by DiskEdge on 2006-08-13
Thanks for your suggestions but I think I will just run it in Safe Graphics Mode.  The resolution this produces is very good (looks to be 1024 by 768) so it is definitely workable enough for me to check out Ubuntu and decide if I wish to pursue it furthur.

---

