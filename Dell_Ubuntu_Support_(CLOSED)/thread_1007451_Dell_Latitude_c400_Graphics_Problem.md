---
title: "Dell Latitude c400 Graphics Problem"
date: 2008-12-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Alexzander J. on 2008-12-10
I have a Dell c400 Pentium III 866Mhz with 256ram, and a Intel 82830M 48mb built in graphics card. It doesn't have a cd-rom or floopy drive and will not boot from USB. I got it for $90 because it had a corporate Windows XP that was completely locked and wouldn't even let me change the  desktop's background. I connected it to a desktop computer through a network and installed windows XP home using the cd-rom on the desktop. It works great, however I have been playing around with Linux for a couple weeks (on another computer) and I think it would be Ideal for my old laptop. I like the idea of a duel boot because I'm on a windows network and am at this point more comfortable using windows for networking. I have Installed Ubuntu 8.10 using the "install in windows" option and it went fine until I reboot and Ubuntu says it's installing the system. During the system install my screen changes to vertical bars (like a failed graphics card)and completely locks up. I have to hold the power button until it shuts off and if i try to reboot ubuntu it goes through the same process of installing the system all over again, just to once again freeze. Is there a safe graphics mode that can be activated before it installs or a file that I can modify while in windows? If anyone has any ideas please let me know.

---

### Post by harleymick on 2008-12-11
Hi,
I have exactly the same machine and had the same problem.
What I did , after several attempts to have Ubunto 8.10 installing with lots of crashes was,
 insert a USB mouse, 
have Ubunti installing in safe graphics mode.
It should do the installation without problems.
Afte installation you can adjust the screen/graphis parameter.
Afterwards you can disconnect the USB mouse.
Ubuntu 8.10 runs very stable on my C400.
I also have a PCMCIA card installed for wireless.
I am just mentioning it, may be it also plays a role.

Cheers

---

### Post by sayantandas on 2009-01-01
> **harleymick said:**
> Hi,
I have exactly the same machine and had the same problem.
What I did , after several attempts to have Ubunto 8.10 installing with lots of crashes was,
 insert a USB mouse, 
have Ubunti installing in safe graphics mode.
It should do the installation without problems.
Afte installation you can adjust the screen/graphis parameter.
Afterwards you can disconnect the USB mouse.
Ubuntu 8.10 runs very stable on my C400.
I also have a PCMCIA card installed for wireless.
I am just mentioning it, may be it also plays a role.

Cheers

how would u install ubuntu 8.10 in safe graphics mode.?
there is no such option. can u please explain in detail?

---

### Post by Jeroen de Lange on 2009-01-20
Already posted this somewhere else, but it seems u have the same problem I struggled with. Just got my machine working and am running all the updates now. Hope it doesn't freeze on me or goes white screen again on me. I think the videocard is the problem, I found my solution here:

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/196900](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/196900)

It's a fun little machine and quite high powered 4 its time so I hope u get it working :popcorn:


Intrepid Ibis on a Dell C400
OK, I've got an old Dell C400 without an external CD-Rom.
So I copied the Ubuntu system to a stick and chose for double boot
Windows + Ubuntu

It took 4ever to install and when it was installed I got a white screen after logging in. I could see my cursor though.

What I did to solve this problem (with a little help from the web)
was

==> Choose Ubuntu (remember, dual boot)
==> Press Escape within a few seconds and go 4 Ubuntu 8.10 (recovery mode)

(U get all kinds of fun little letters that fly by so fast u can't read them xcept Activating swapfile. It ends up with a lovely blue screen)

==> Go to root and Enter

Then follow these instructions:

2) sudo pico /etc/X11/xorg.conf
3) Add the following:
Section "Extensions"
Option "Composite" "disable"
EndSection
4) save file, quit pico, logout.

---

### Post by zulunet on 2009-01-28
Dude you rock, thanks this worked just it is case ses.
thanks so much

i love my c400 but the no usb boot suchs.

zulunet

---

