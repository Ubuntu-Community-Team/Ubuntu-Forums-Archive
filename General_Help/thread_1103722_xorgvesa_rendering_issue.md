---
title: "xorg/vesa rendering issue"
date: 2009-03-23
forum: General Help
---

### Post by utnubuuser on 2009-03-23
This is a duplication of an "other OS" thread. - got no response there.

Hi -- I'm experiencing some graphics rendering problems on an older P3 Pavilion laptop.

At startup the desktop is alright, and after a while degrades slightly.  
I've attached a screenshot to show the effect. -noticeable in the top-right corner.
I'm wondering if I should change to the VESA driver maybe, and how-to?
This machine only shows 247megs of ram, so that might have something to do with it.
The OS is the new Lenny, because it's the only one, besides Puppy, that would even load.
Any suggestions?

Let me know if lspci or dmesg print-out would help. Thanks

P.S. I've done the usual dpkg-reconfigure to see if that would help, without effect.
Re-starting the xserver with ctrl+alt+backspc usually clears it up.

---

### Post by kerry_s on 2009-03-23
sounds like you got a low spec machine and from that pic you are loading her up.
what are your specs? or what model Pavilion laptop, so we can look it up.

---

### Post by utnubuuser on 2009-03-24
Hi kerri_s

Yeah, it's a pavilion n5445 with a 1ghz processor and only 256mb ram.

I'm scoping around for a larger ram module to see if that'll make a difference.

I had to install Debian Lenny, - none of the Ubuntus got past the kernel load screen. and Debian only installed through the net install minimal install, then added xorg and desktop afterwards.
Other than the rendering issue the laptop performs quite well.

---

### Post by kerry_s on 2009-03-25
you should have gone lighter than gnome, example:
su
apt-get install xorg gdm lxde

but anyways, why aren't you using the intel driver for video?
example:
su
gedit /etc/X11/xorg.conf

```
Section "Device"
        Identifier "Intel Graphics Adapter"
        Driver     "intel"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device "Intel Graphics Adapter"
EndSection

```

i suspect that using the wrong driver is causing the rendering issue, vesa driver is a very basic catch all driver. using the right driver is the first step.
using lighter setup/programs will make things a heck of a lot faster. i used debian for years on my 450mhz 256mb ram laptop, now i use arch linux.

---

### Post by utnubuuser on 2009-04-11
Thanks --  I've got the Intel driver installed and the system is doin' ok.  I'm fairly sure it's just a matter of getting a bit more ram on board.  The 256 isn't enough for Gnome - as you were saying - I used Gnome because Gnome is the environment I like.  I've tried KDE and XFCE, and find that Gnome functions as I'd expect  my desktop to.

---

