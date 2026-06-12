---
title: "ppracer not showing menu/low framerate in Feisty!"
date: 2007-05-06
forum: Gaming &amp; Leisure
---

### Post by Turin Turambar on 2007-05-06
:( Ppracer worked in every ubuntu release, but in feisty there are load of problems.
Menus are not working (see the attached image) and the game is very slow and not playable.

I have a Radeon 9000pro card, using "radeon" driver i Xorg. I tried disabling compiz, but no effect.

---

### Post by Perfect Storm on 2007-05-06
Have you tested your card with other 3D games?

---

### Post by Turin Turambar on 2007-05-06
No.
You see, I don't really play games. PPracer and Frozen bubble are the only games outside the GNOME package that I enjoy playing.
Tux racer worked from Hoary to Edgy without any problems. In fact, in Edgy it worked even with the open source "radeon" driver (that was not the case with hoary/breezy/dapper, where a dedicated fglrx driver had to be used in order to have full 3d accelerated support).

In ppracer I see the snowflakes falling quite smoothly, which means that 3d support is working. But unfortunately, the game is extremely slow.

---

### Post by Perfect Storm on 2007-05-06
Perhaps you should check the howtos on ATI cards, there could be some complication with the driver in Feisty, or search the forum with similiar problems.
Though I can't help you there as I'm a long time user of Nvidia.

---

### Post by nullix on 2007-06-04
i hit problems upgrading feisty with my radeon RV250 9000 with a Asus vintage motherboard.
It was running on previous dapper.
Since direct rendering was not running ppracer was very slow (unplayable), but worked with menus.

to make it work again i did :
use ati driver in xorg.conf ( provided with xserver-xorg-video-ati package normaly installed by default)
renamed sis_agp.ko to sis_agp.ko.bak since it prevented AGP detection of my card by driver, this is due to a problem with my motherboard, seems 2.6.20 sis agp driver create problems.
since then i could see direct rendering enabled in /var/log/Xorg.0.log ("(II) RADEON(0): Direct rendering enabled")
But still direct rendering was not working with games ( i found error using LIBGL_DEBUG=verbose glxinfo ) it complained about a r200.lib ... this was duer to fglrx installation ( the proprietary driver, that doesn' not supported those too old card we have ).
then i removed it : sudo apt-get remove --purge fglrx-control xorg-driver-fglrx xorg-driver-fglrx-dev

Then ppracer get to a normal speed, but i have lost menu, instead i have ugly dotted lines.
This problem appear with direct rendering enabled.

---

### Post by schadfield on 2007-06-11
> **Artificial Intelligence said:**
> Perhaps you should check the howtos on ATI cards, there could be some complication with the driver in Feisty, or search the forum with similiar problems.
Though I can't help you there as I'm a long time user of Nvidia.

I doubt this is ATI specific. I see the same problem with my Matrox G550.

---

