---
title: "dell 1210 screeching sound"
date: 2009-09-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by the_martian on 2009-09-15
My daughters'  dell 1210 has just started making a loud screeching noise when we turn it on, the noise starts as ubuntu is starting up and is loud and continuous. We've run diagnostics as directed by dell support and confirmed that  hardware is ok (I was worried it was hard disk, but it seems not),  so their next suggestion was to re-install ubuntu, which I thought was a bit extreme and don't see why that should solve it.  I've noticed that I can mute the speakers and the sound stops and the machine is running absolutely silently until I unmute again. I'm really puzzled what could be causing this.  The machine was bought in July and has been fine until today.  

Has anybody had something similar happen?  ( I have searched the forum, but not found anything) Is it likely that the on-board sound chip is duff? 

Any answers gratefully received, but keep them simple please - I'm stuck on Windows, dont know a lot about Ubuntu and my UNIX knowledge is several years out of date. 

thanks in advance

Martin

---

### Post by pablo180 on 2009-09-16
If I were you I'd download the [Ubuntu Live CD]("http://www.ubuntu.com/GetUbuntu/download"), once downloaded either burn it to CD if you have an external drive or in Ubuntu click System > Administration > Create USB Startup Disk and plug in a 1GB or more USB stick (that you don't mind wiping). Then with the USB stick or CD in start the laptop up. 

You should get a screen come up asking if you want to try Ubuntu without changing your system, just press Enter (Don't select the option to Install). 

If you don't get that screen and it boots into Ubuntu as normal, try hitting F12 when it starts and then select Boot from USB or CD (if you have one). 

That will boot up an entirely separate and new installation of Ubuntu from the CD/USB stick, without affecting the one you have installed and without having to re-install Ubuntu. If you still get the same sound, it is then most likely a hardware issue, you should then contact Dell and tell them you have the same problem on a new installation. If you don't get the same sound, then it is probably something to do with your installation of Ubuntu. 

I still wouldn't re-install though if I were you, you'll probably just need to re-install the drivers for the sound. I have no idea what drivers the Dell 1210 uses, but you may find some help here [Dell Linux Support]("http://linux.dell.com/wiki/index.php/Products/Consumer").

---

### Post by the_martian on 2009-09-17
Thanks for the reply Pablo.   In the meantime I've been back in touch with Dell and I've entrusted the laptop to their tender? care as its still under warranty and I'm pretty sure its a hardware issue.  I'll use your tips about making a bootable pen drive so that I've got some other options if we get problems in future.

---

