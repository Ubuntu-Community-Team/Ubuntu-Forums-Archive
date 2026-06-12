---
title: "Screensaver freezes every time"
date: 2006-02-27
forum: Desktop Environments
---

### Post by Heretic Monkey on 2006-02-27
I'm using the AMD-64 distro of Ubuntu (breezy), and i'm not really having any problems not to be expected of the 64-bit version... except one.

Everytime my system cuts to the screensaver, it'll run for a few minutes, then just completely freeze.  It doesn't matter what the screensaver is, i've tried the most advanced graphix to the most basic, but they all do the same thing.

I'm using an ATI Radeon Xpress 200 integrated card (stock box, yeah, shutup..... lol).  Is there any way to fix this problem?

*EDIT*= I'm using Gnome, and when the screensaver freezes, my system is still fine (i can exit the screensaver with no problems).

---

### Post by Bartender on 2006-02-28
HM -
Is this a notebook we're talking about?  The screensaver lockup seems to be an ATI problem.  I switched my desktop ATI 9200SE to a low-end nvidia card and prob went away.  That doesn't help you much if you've got a lappy...

---

### Post by Heretic Monkey on 2006-02-28
Nah, it's on a desktop.  Is there a way to fix the problem through software settings, maybe a driver config or something?  I'm still a linux noob, so i'm not sure how to go about changing the drivers or anything.  I know linux and ATI aren't the most compatible objects, but if there's a way to keep the screensaver from freezing, i'd love to hear it.

---

### Post by Bartender on 2006-02-28
There may be...I posted a few weeks back asking about this & got no replies.

---

### Post by Bartender on 2006-02-28
If nothing else, you may want to turn off screensavers...

[COLOR="Blue"]It's possible with xscreensaver-command. To deactivate the screensaver, type

Code:

xscreensaver-command -deactivate

Take a look at the manpage for more options. This is a very flexible tool for use in scripts.[/COLOR]

Borrowed the above from another thread.  Found it by doing a Search for "screensaver"

---

### Post by Heretic Monkey on 2006-02-28
Yeah, i have had them turned off for a while...... just wish there was a way to fix it so i wouldn't have to keep turning my monitor off and on.....

---

### Post by pbaehr on 2006-02-28
I have an onboard ATI Radeon Xpress 200 video card and experienced the same problem (along with many others).

My solution: Add an NVIDIA video card to the system and use that. It worked like a charm.

I realize this is not the solution you are looking for but it will save you many headaches down the road. I'm guessing that your 3d acceleration is also not functioning?

---

### Post by Heretic Monkey on 2006-02-28
Haven't really used any applications that require 3d accel yet.  I dual boot with XP, and still play all my games on my windows partition (as well as a crap load of programs i need for school).

If the only solution to the screensaver problem is to add more hardware, i guess i'm going without a screensaver...... i'm completely broke at the moment, and don't feel like spending money on another card (that i need anyway)....

---

### Post by pbaehr on 2006-02-28
All the default screensavers seem to use hardware acceleration. As the Radeon Xpress 200 seems to have severe problems with hardware acceleration I wonder if the problem lies there.

Are there more basic screensavers that could be installed to replace the default ones? I wonder if that would solve the problem.

I never messed around with it but maybe someone else can point you in the direction of somewhere you could get some more basic screensavers.

---

