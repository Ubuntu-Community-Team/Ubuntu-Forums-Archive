---
title: "Uneven fonts sizes in some non-Qt applications"
date: 2011-07-20
forum: Desktop Environments
---

### Post by street spirit on 2011-07-20
I have a relatively fresh install of Kubuntu 11.04 here. Generally everything looks very nice (even without the desktop effects, which I had to turn off for now), but I noticed that some applications which use a different GUI toolkit than Qt have rather large fonts:

[IMG]http://i.imgur.com/Rsucs.png[/IMG]

The windows, from top to bottom are:
- Firefox
- Opera
- GIMP
- Dolphin
- BeyondCompare

Dolphin is native Qt, so no problems there. Firefox and the GIMP look nice, too, probably due to the GTK+ widget integration in KDE. Opera and BeyondCompare, on the other hand, use much larger fonts than the others. They are both closed-source, proprietary programs, so I'm not sure which GUI-toolkit they use; could be Motif in Opera, and whatever Kylix used in BC.

This is a very minor, purely aesthetical matter, but I was wondering if it was possible to make those two fit in better, because I use them all the time.

By the way, the GIMP wouldn't even start at first (segfault) until I followed the advice given elsewhere in this forum and changed the GTK+ widget style to Raleigh, opened the GIMP, and then switched back to oxygen-gtk.


PS, if all of the fonts in the screenshot look large to you, that's because they are. This laptop has a 1920x1080 resolution on a 15" screen - nice engineering, but the resulting default font size makes me squint even when I'm only 17" away from the screen :)

---

