---
title: "OpenGL Screensaver (half screen)"
date: 2006-10-15
forum: Desktop Environments
---

### Post by Bizmac on 2006-10-15
Hi all, is there anyone knows why did my GL Screensaver just shows half of my screen? I try to use Pendulum, Gravity, etc but only Space that shows full screen. I've check my openGL and run just OK, smooth like silk.

---

### Post by orb9220 on 2006-10-15
Need to post your video card type and what drivers you are using.

---

### Post by Bizmac on 2006-10-16
My video card is an Intel i810
My driver is a VESA generic.
I tried to switch to i810 but the interface crashed.

Can it help?

---

### Post by orb9220 on 2006-10-16
Well to get 3d and opengl screensavers to work you have to get the drivers specific to your chipset installed.

Vesa driver is like the default drivers in xp they work Kinda.

---

### Post by DarkN00b on 2006-10-17
I am assuming you have installed the i810 driver from the repositories befere changing your xorg.conf. If you haven't then by all means install them before changing your xorg.conf.

I can't imagine why this would happen if you are using the i810 driver that is in the repos. I have installed Dapper twice and it has worked like a charm both times. You might try going into Synaptic and marking the i810 driver for complete removal, then reinstalling and switching from "vesa" to "i810"in your xorg.conf.

I've never had too much trouble with mine so I'm sorry I can't help more.

---

### Post by Bizmac on 2006-10-17
Ok thank you for your help.
It is now working well!

I try to install AIGLX but fail, will try again later if anybody knows a good  HOWTO install it?

---

### Post by ringmaster on 2006-10-19
I am having the same problem with a SiS630 chipset, I tried with the driver included with x.org, and I tried to compile the driver into the kernel, even I tried to install the latest drivers (SiS300 series driver) from Thomas Winischhofer, but with the same results. Only half screen in programs at fullscreen (those drawn in a window works ok). I am going to install Dapper again and try knoppix... If I found a solution I'll post it.

---

### Post by Unicast on 2006-10-25
I was having problems with the OpenGL screensavers on my Dell D400 running Dapper - Intel Corporation 82852/855GM integrated graphics and i810 driver. But on upgrading to Edgy (fresh install actually) I'm having no problems at all! :D

---

