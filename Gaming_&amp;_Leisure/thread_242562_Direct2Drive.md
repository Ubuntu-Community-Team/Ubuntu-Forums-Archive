---
title: "Direct2Drive"
date: 2006-08-23
forum: Gaming &amp; Leisure
---

### Post by pollock.tar.gz on 2006-08-23
i was wondering..is it totally impossible to play direct2drive games on linux? i have Civilization IV from it, and really would like to play it on ubuntu..

---

### Post by Toxicity999 on 2006-08-24
How do they work is there some kind of custom launcher or do they basically give you CD rips? I assume it's packed in some weird way... If that's the case the trick is making whatever They use to launch the games make front. Best thing to do is try I suppose... But my personal tip when these big companies start up something like this it's near always some pain in the *** packaging, or some kind of lock ie itunes.....

---

### Post by samichx on 2009-02-21
Excuse me if some of this seems redundant, I had a younger family member that grew up with Linux ask me about this after he tried to 'Google' the solution. D2D is a windows oriented operation as of this post, so here is the explanation.

Direct2Drive works a lot like the deb system*, in its simplicity. Get the installer, install, and play. The differences include the fact that the application and its libraries are sent as a combined installation file because that is how Windows operates traditionally. (ex. Pidgin installer is packaged with libpurple for the Windows install)

Ubuntu could perform these download and install operations, and it is possible that pre-configured Wine ports could be downloaded through apt systems. The problem is payment and unlike Steam or WiiWare there is no existing way to securely share commercial deb files** for Ubuntu (that I know of). 

You CAN buy Wine or Cedega compatible installers - but really look into compatibility before plunking down cash. False positives have been known to pop up when transitioning between CD/DVD to Downloadable installations. Also, though I added this for the benefit of someone younger be sure to check out the Terms and Conditions at D2D, as well as those from game publishers.

* The 'deb' system is the packaging, transmission, and installation sequence you may use aptitude or synaptic to use.
** 'deb' files, though used in the deb system can be installed independent of the apt system through dpkg or gdebi

Addition: Even though D2D is online and Synaptic is a desktop app they DO perform the same functions - find, select, and download. The installation part is still outside of both systems.

---

### Post by Vadi on 2009-02-22
Only thing I used D2D for is buy the windows version so the linux installer could have the data files it needs.

I ran into some issue with their purchasing system, and the reply took 48+ hours - totally not satisfatory, so I couldn't recommend this to anyone.

---

### Post by Cresho on 2009-02-22
Direct2drive uses a DRM type scheme to lock the particular software to your hardware.  It needs internet to unlock the software along with serial key...etc.  This is the copy protection they use.

When I purchased oblivion, I had problems unlocking it when I disconnected my pc.  I asked them why I needed the internet when I had the download on a cd.  THey told me about the copy protection scheme they use.  I asked for my money back and purchased the DVD version instead.

---

### Post by lovinlinux on 2009-02-22
yea,
I had to end up using a no-cd patch after i purchased oblivion from D2D.

---

