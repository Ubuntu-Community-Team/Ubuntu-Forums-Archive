---
title: "Need Help with Blank Screen After Install"
date: 2005-12-27
forum: Desktop Environments
---

### Post by Hangetsu on 2005-12-27
I have an older machine with an old NVidia card.  The installation is complete, boot up seems to go fine, then I get a frozen cursor in the upper left hand corner of the screen.

I think its related to the video card's configuration, and I read up on it here on the boards.  I went to go take a look at the xorg.conf file to find I don't have an X11 directory under /etc!?!

Gnome was set up, so I'm not sure why the underlying X Windows system would be missing (if it is).  Any ideas on how to get this to work?  I installed edubuntu 5.10 for my daughter's machine.

Thanks!

---

### Post by stuporglue on 2005-12-27
At the grub menu, boot into rescue mode. It should give you a root prompt. 

Type:
# dpkg-reconfigure xserver-xorg

It should start a dialog about 20 screens long reconfiguring X for you. If it doesn't work (if you really don't have an /etc/X11 for example) try doing "apt-get update" then "apt-get install edubuntu-desktop" and see what happens.

---

### Post by Hangetsu on 2005-12-27
OK, the exact card installed is a GeForce4 from nVidia (MX440SE 64MB).  Its been a while since I've used this particualr machine so I forgot (its been my daughter's for over a year).  I have no idea how to get this particular card working (it seems to autodetect the on-board Intel graphics chip -- not exactly what I want!)

I looked up this card here on the forums, and it talks about installing the nVidia drivers via Synaptic.  Since I can't get into the GUI environment, I'm at a loss for how to get my xorg.conf configured (yes, true newb here).

Anyone have a link or mind laying out the steps, in small words and slow talk?  *grin*

Thanks for the help!

P.S.  I should mention that my networking is still down as well on this box (I need to set up the ndiswrapper for the card I have -- worked great with a little help on another machine).

---

### Post by Hangetsu on 2005-12-27
**[SIZE="5"]EUREKA!!![/SIZE]**

I ran an apt-get for the nvidia drivers, which installed.  Then, I was able to use that within the dpkg-reconfigure xserver-xorg for use with my card.

That initially didn't work -- It kept defaulting to PCI:0:1:0 for the bus location, but the logs showed that there was no device listed in the xorg.conf file for PCI:1:9:0 -- that's a problem.  The reconfigure wouldn't allow me to USE 1:9:0, and that may be a bug.

I made the change in the xorg.conf file itself using vi, and voila, I'm in!!!

Thanks much for your help!

---

### Post by infoseeker on 2005-12-27
Did you disable the on-board (Intel) graphics in CMOS ?

---

### Post by Hangetsu on 2005-12-27
No, and I think that's what threw it off.  Its not using it now, so I think I'm good .

---

