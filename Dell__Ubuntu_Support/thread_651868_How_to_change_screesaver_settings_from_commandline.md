---
title: "How to change screesaver settings from commandline"
date: 2007-12-28
forum: Dell  Ubuntu Support
---

### Post by manmohanpv on 2007-12-28
Hi Frnds

I have a problem with my screen saver application under preferences>screensaver

When ever i open it, linux hangs...i think the screen saver selected by default causing this issue.

It happened after i installed a screen saver GLMatrix and now i want to change the screensaver to dubuntu efault. But i can't do as my system hangs as soon as i open the screen saver dialog

So, i'm looking for some commands to change the screen saver settings of my dell inspiron ubuntu 7.04 system through terminal

Any idea where linux stores the config files for screensavers in ubuntu 7.04?

Any help appreciated

-thanks
manmohanpv

---

### Post by natehall on 2007-12-28
Type in  gconf-editor. Then click on apps, Then on gnome screensaver. On my 1420n certain 3-d screensavers froze my computer because I did not have the proper video driver. The Dell factory DVD I used for Ubuntu 7.10 (Gutsy Gibbon) fixed that.

---

### Post by manmohanpv on 2007-12-29
Excellent Natehall!

I could able to resolve the issue with your tips. May be a little explanations will help people, so quotting below:

Guys,

Launch gconf-editor

Go to Apps>Gnome screensaver

Change the variable Mode=blank-only

Next time when you launch preferences>screensaver, the default will be a blank screen which will support any video card

Cheers
manmohan

---

