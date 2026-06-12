---
title: "Sound on IBM 600X"
date: 2005-05-26
forum: Desktop Environments
---

### Post by Frihet on 2005-05-26
I've been working on my sound problem for a while with no success. I found this at
[http://panopticon.csustan.edu/thood/tp600lnx.htm#secsnd:](http://panopticon.csustan.edu/thood/tp600lnx.htm#secsnd:)

The 600X has a Crystal Semiconductor CS4614 chip. 

Under Linux 2.6 the ALSA drivers work well; however as of April 2005 they still need to be reloaded after an APM suspend-and-resume cycle because their power management support isn't working.  To deal with this, get the very latest alsa-base package (1.0.8-4 as of this writing) and set force_unload_modules_before_suspend=snd-cs46xx in /etc/default/alsa.  If you are using GNOME then you should ensure that esd releases the sound device after playing a sound; to ensure this, make sure that it gets started with the "-as 1" option.

I'm assuming I apt-get alsa-base install to do the first part, right? I have not done that yet because I don't know what version HHH uses (up to date with universe enabled) or what I'd get if I did the apt-get.

I found the force_unload line and modified it as directed. That did nothing.

Since I'm Kbuntu, I ignored the esd item (Ubuntu Gnome will not run at all on the 600X).

Comments?

Thanks!

---

### Post by Frihet on 2005-05-26
I found the installed alsa-base version.  It is 1.0.8-4.  So, I guess this lead is a dead-end.

---

