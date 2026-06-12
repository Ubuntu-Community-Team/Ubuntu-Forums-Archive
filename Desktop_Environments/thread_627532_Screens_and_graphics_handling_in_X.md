---
title: "Screens and graphics handling in X"
date: 2007-11-30
forum: Desktop Environments
---

### Post by farbror_ace on 2007-11-30
Hi

Im pretty new to Ubuntu/Linux but Ive managed to get dual screens going (laptop with external lcd) on my ATI card.
But now I use my laptop at another location without an external monitor, and no matter what I print in my xorg.conf X still boots up with a 2800x1050 desktop.

What is the order of X loading settings and where can I find additional settings apart from xorg.conf?
There is no configfile in my entire X11 folder that contains 'virtual' or 2800 resolutions, still it boots with a 2800x1050 desktop.

Im pretty stuck here..

---

### Post by phidia on 2007-11-30
It would seem unlikely that that resolution isn't in /etc/X11/xorg.conf however you could check /var/log and all the xorg messages there. Maybe there's a clue to this there?

Have you tried issuing "sudo dpkg-reconfigure xserver-xorg" Do that from terminal when you're booted with just the laptop screen and select the correct specs and see if that helps.

---

### Post by farbror_ace on 2007-12-06
Thank you for your reply I guess my question became abit fuzzy due to lacking knowledge.

Ive played with this a little further now and found the tool xrandr.
A very useful tool indeed but some things dazzles me with this.

When I dont use fglrx xrandr -q reports 2 screens and I can manipulate the screens fully. Turning them on/off moving them left and right etc etc.

But when I load fglrx fglrx seems to 'emulate' the hardware layer and xrandr basically reports what the ati catalyst control center has set.

F ex if I set dual desktop in ati catalyst control center xrandr reports 1 default screen with the resolution 2800x1050.

I would really like to use fglrx since the 3d on it is much faster. But I get much better control over my screens if I dont use it.

Help appreciated!

ace

---

