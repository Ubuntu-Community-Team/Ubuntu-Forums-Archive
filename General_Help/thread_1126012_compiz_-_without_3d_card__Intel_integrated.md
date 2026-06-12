---
title: "compiz - without 3d card?  Intel integrated?"
date: 2009-04-15
forum: General Help
---

### Post by u.2 on 2009-04-15
Hi,
Can I run compiz without a dedicated video card?  I have a Dell laptop which has an integrated intel video card.  I thought it supported 3d acceleration, but from another post I read it appears this card may not do 3d graphics.

How can I find out and if it doesn't then will compiz still work?  I have tried installing some emerald themes and it doesn't seem to work right.

The top and bottom panel's dont' change color, and the fonts seem to get messed up a bit.

---

### Post by Ravernomina on 2009-04-15
i have a dell, Intel card that's 5 years old and does the cube and every other compiz animation your good to go mate :).

---

### Post by stumbleUpon on 2009-04-15
Check if your system can run compiz using the script from here

[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

---

### Post by Psychopump on 2009-04-15
Yeah, my laptop has intergrated intel graphics and compiz works 100% - all effects and cube look great (especially wobbly windows while running a video).

Most 3D games won´t work for me though, neither will ProjectM. :(

---

### Post by madhi19 on 2009-04-15
Anybody know what the bare minimum for compiz because am SOL with my rage fury integrated card. And yes it probably way time that I upgrade the old horse but it still working and am not spending money just for compiz.

---

### Post by u.2 on 2009-04-15
THX!  Here is what I get from that script.  I have no idea why I am suffering/struggling.

I can't even get my dual monitors working.  I have one 19inch widescreen that should work fine at 1600x1200 or at least 1440x900 and I can't get that to go past the 1024x768, and on my laptop screen the whole screen isn't in use?

Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [WARN]

Something potential problematic has been detected with your setup:
 Warning: PCI ID 8086:2a02 detected. 

Would you like to know more? (Y/n) y

 Your particular graphics chip may be blacklisted on certain distributions.
 However that does not necessarily mean you will not be able to run Compiz.

 You can skip this blacklist -- but keep in mind that you did so.
 Do not complain if you encounter any problems with Compiz afterwards. 

Do you want to skip blacklist checks by Compiz? (y/N) n

---

### Post by mark1124 on 2009-05-15
Hi, Psychopump.  Can you post a copy of your xorg.conf file.  I ran the compiz check and everything is 100% [ok] to run compiz.  However, when i enable desktop effects everything on my screen disappears but my wallpaper.  I'm running on a Dell Inspiron 1100 with a P4 (2.4GHz) and 1 GB of ram with 845G chipset.

Ubuntu 9.04

---

### Post by fragos on 2009-05-16
I've a Dell 1420n and at one time the Intel video was blacklisted by Compiz but that was a number of Ubuntu releases ago. I believe it started working with Compix with Ubuntu 7.10. It certainly works withe 9.04 I run now. Compiz uses more CPU than Metacity so I've disabled Compiz on my laptop to maximize battery life.

---

### Post by Psychopump on 2009-05-17
> **mark1124 said:**
> Hi, Psychopump.  Can you post a copy of your xorg.conf file.  I ran the compiz check and everything is 100% [ok] to run compiz.  However, when i enable desktop effects everything on my screen disappears but my wallpaper.  I'm running on a Dell Inspiron 1100 with a P4 (2.4GHz) and 1 GB of ram with 845G chipset.

Ubuntu 9.04

I would love to, but I have caught the *nix bug and am now a number of distros further down the road.
I will be changing to Mint Gloria later today, if I get Compiz running on that I'll post my xorg file.

---

