---
title: "Xpress 200M hdtv output"
date: 2010-11-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dr_duck on 2010-11-01
Hi I have an inspiron 1501 (Turion X2 64bit, 2Gb ram, Xpress200M integrated graphics) running Maverick 64bit.

I'm using the opensource radeon driver which works well - I can get desktop effects (both 'normal' and currently via compiz).

I have recently got an hdtv (LG 42inch plasma, 720p) which has a vga input.

If I connect the laptop to the tv via a vga cable, gnome seems to automatically recognise this (I did not need to log out or anything) & sets up the tv as a secondary monitor (not cloned).

My problem:  If the display is set to 'extended' (ie not cloned) then the picture on the hdtv is very messed up.  I can't get a screenshot but its like this:  The laptop display stays the same (widescreen 1280x800), the hdtv gets set to 1280×720 (this is the correct res for this tv) but the rightmost third of the picture is black.  I can move my mouse over there, but there is no 'desktop' - I can't click, windows turn black when I drag them over there & there is a bit of my panel in there massively zoomed in...

If I set the display to be cloned, my laptop screen stays the same res, and the hdtv also gets set to the same res so it looks all streched & fuzzy.  It does work though.

So:  When set to extended (what I want) the display is garbled.  There's nothing in Xorg's logs that I can see which looks wrong.  Any ideas?

EDIT:
If I log & reboot out while the tv is connected, the laptop display goes dark & gdm is displayed on the tv (again, the rightmost third is black).  Logging in gets me to the above situation.

Just to clarify, when I says the rightmost third is black, its not that the desktop is scaled to only the left 2 thirds, the desktop res looks correct but it seems like the right third is just not being drawn at all, and there are 'artifacts' in there (eg bits of the panel, randomly zoomed in)

---

