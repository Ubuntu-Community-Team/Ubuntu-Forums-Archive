---
title: "error while installing BERYL - issue with xorg.conf"
date: 2007-09-22
forum: Desktop Effects &amp; Customization
---

### Post by stork123 on 2007-09-22
I am playing around with installing BERYL using this guide [http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon") i think i editing the xorg.conf file poorly and now ubuntu fails to boot. I'll boot again soon to give you a better idea of the error message but it pertains to the graphics card.
I'd like to revert xorg.conf back to the previous state but don't know how to edit it.
I am booting with a live cd - and when i edit the file - i am told "You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again." this is the file on the harddrive - not the live cd. I'm assuming i need to login in to edit this file?
I am trying to edit with Gedit

More importantly - by undo'ing the edits I made - will this fix it?

---

### Post by FuturePilot on 2007-09-22
If you know exactly what you added, then yes removing what you added or edited should fix it.
You must use Gedit as root like so
```
gksudo gedit /etc/X11/xorg.conf
```
 But if you don't remember everything you did, the best thing to do would probably be starting from scratch with a new xorg.conf file. The easiest way would be to do this
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by stork123 on 2007-09-22
great! just did it.

I got 


xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20070922090618



gonna reboot now out of the live cd and see what happens.
thanks for the quick reply.

---

### Post by stork123 on 2007-09-22
no luck - I'll post more clues when i get back from cheering a friend on at a donkeykong tournament.

When using Gedit after booting with the livecd and I editing the xorg file of the harddrive? 




and what about these commands from the online guide:

We want to use AIGLX with open-source ATI driver instead of XGL with the proprietary ATI driver (fglrx). Therefore we have to disable fglrx. First we disable the fglrx kernel module:
_____
sudo modprobe -r fglrx
______
Then we run

_______
glxinfo | grep vendor
_______



Do I need to undo these commands?

---

