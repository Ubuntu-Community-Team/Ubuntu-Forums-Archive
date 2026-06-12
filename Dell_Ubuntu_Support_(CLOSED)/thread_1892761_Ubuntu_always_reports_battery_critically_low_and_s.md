---
title: "Ubuntu always reports battery critically low and suspends/shuts down my Inspiron."
date: 2011-12-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by BHTX84 on 2011-12-08
I've had this problem since with Ubuntu since day 1 with 10.04. I always just assumed there was a fix around the corner. Unfortunately, I'm still waiting.

Every time the AC power is unplugged (especially a problem when you have the common issue of the power cord falling out all the time), power management seems to think my battery only has seconds of life remaining, and a message pops up warning me that my battery is critically low. For whatever reason, there's a Cancel and an OK button on this popup, which makes no sense. Regardless of which button I press, or if I even press a button at all, my laptop suspends or shuts down within seconds (depending on the setting in Power Management).

I have yet to come across a fix that actually works, other than disabling gnome-power-manager in Startup Applications. However, upon doing that, I lose any control of screen brightness setting (which I use often), and of course any indication of battery charge.

I came across an old bug report earlier which stated that this wasn't really a problem with gnome-power-manager, but rather an issue with something called "upower".

Any idea how to finally resolve this problem?
Btw, 10.04 LTS is currently installed, although I've also had this problem with 10.10 and 11.04. I haven't tried 11.10, but I'm assuming nothing has changed.

---

### Post by BBQdave on 2011-12-08
How old is the battery?

Was given an inspiron 1100.  The first two things I did was new battery and maxed out the ram.  Installed Ubuntu 10.4LTS, good machine no worries.  Then installed **Debian6**, now I have a great machine, pushing a decade of use :D

---

### Post by BHTX84 on 2011-12-09
> **BBQdave said:**
> How old is the battery?

It's an N5010 (Inspiron 15R) with a Core i3. Last I checked, it was still being sold. So, a few months maybe? Less than a year. Regardless, the battery does hold a charge. Ubuntu just doesn't think so.

---

### Post by aa-hcl on 2011-12-10
Hi,

I have dell E6520 and had similar problems.I am running 11.10.
The problems were since installation of 11.10, but several days ago after a big update, the problems seems to be solved.

---

### Post by BHTX84 on 2011-12-11
> **aa-hcl said:**
> but several days ago after a big update, the problems seems to be solved.

Oddly enough, I also received an update through Update Manager 2 days ago. I can't recall the name of the package, but it seemed to be something related. Since then, I haven't encountered any of the usual issues when starting the gnome-power-manager. So, I just now re-enabled it in Startup. Kudos to anyone involved. Hopefully it'll stay this way.

---

### Post by BHTX84 on 2011-12-11
I take that back. It just screwed me over in the middle of a movie. :confused:

---

