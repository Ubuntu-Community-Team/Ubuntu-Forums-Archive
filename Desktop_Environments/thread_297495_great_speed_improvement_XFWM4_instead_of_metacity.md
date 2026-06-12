---
title: "great speed improvement: XFWM4 instead of metacity"
date: 2006-11-11
forum: Desktop Environments
---

### Post by patrickfromspain on 2006-11-11
Hi there! On my laptop, I've never been 100% satisfied by ubuntu... gnome always seemed to be a little to much for this computer (although it isn't that bad: celeron M 1,5GHz, 1gig ram, intel 852gm, 60gigs HDD).

Today I've replaced the standard gnome window-manager, metacity, with XFCE's one, xfwm4. So far, xfwm4 seems to be much more responsive than metacity, while it still is a GTK, so it integrates well with gnome.

Try it!

---

### Post by kerry_s on 2006-11-11
How about simple instructions how you did it? Asking someone to try it with out telling them how is like leaving them out in the cold.

---

### Post by patrickfromspain on 2006-11-11
mm yes, you're right, sorry.

It's very easy:

sudo aptitude install xfwm4

sudo gedit /usr/bin/gnome-wm

look for these lines:
# default-wm value
DEFWM=

and add xfwm4, so that it looks like DEFWM=xfwm4

restart gnome and you're good to go.

Hope I've been clear enough.

---

### Post by ZipoTe on 2006-11-13
Thank you patrick xd

---

### Post by depp on 2006-11-13
use ```
sudo update-alternatives --config x-window-manager
``` instead

---

### Post by smeto on 2006-11-14
how to change xfwm4 decoration theme?

---

