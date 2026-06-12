---
title: "Setting a primary display?"
date: 2009-10-31
forum: Desktop Environments
---

### Post by Chris0134 on 2009-10-31
Hey all,

New to ubuntu, can't figure out how to make the the panels show up on my external monitor, (make it my primary display.)  This is a problem that i didn't have in 9.04.  It is also a pain to have to look at my tiny laptop screen to access the panels; it also is inconvenient having all windows open up in the small screen by default. 

I have tried many display/resolution/mirrored screen options to no avail, I need help.  The only way to rectify this is to turn off the laptop display entirely... not cool.  Could someone offer any assistance?  Thanks.

---

### Post by grj23 on 2009-11-02
Hi

I have a similar problem.  I have a laptop and an external display.  Under 9.04 it's default behaviour (once I unchecked mirror screens in display preferences) was to have the external as the primary and the laptop as the secondary. 

I upgraded to 9.10 and that behaviour has changed so that the laptop is the primary (ie the gnome panels are on the laptop page rather than the external).

I've just discovered (by the extraordinar process of reading the help) that if you hold down "ALT" you can drag the panel to a new spot.  I did this and it moved it effortlessly to the external panel, so maybe that's an easier solution.

I'd be glad to hear what the experts say...

---

### Post by Chris0134 on 2009-11-02
you da man!

---

### Post by therblack on 2009-11-03
I'd love to know how to set the primary display too...anyone?

---

### Post by cynyr on 2009-11-03
see xrandr --output --primary, i don't have a laptop anymore but the --primary should set the external as the primary and then the "panels" and the default window opening location should follow.

---

