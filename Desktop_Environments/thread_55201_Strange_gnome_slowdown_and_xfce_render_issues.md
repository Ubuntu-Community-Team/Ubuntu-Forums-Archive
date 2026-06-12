---
title: "Strange gnome slowdown and xfce render issues"
date: 2005-08-07
forum: Desktop Environments
---

### Post by rosslaird on 2005-08-07
It started a few days ago, without any fanfare: gnome started to drag a bit, then a bit more, and now it's quite slow. Still useable, but slow. There aren't any extra services or apps running. And xfce has started acting up too: odd rendering problems in Firefox and Thunderbird, overall slowness (which in xfce is a serious sign of something amiss).

Only KDE still works as expected. I have been consistently impressed with the kubuntu work, and I guess I'm going to stay in kde for a while.

I don't imagine that I'm going to find a way to resolve the creeping slowness in gnome and xfce. Maybe something frelled the system after an update. Hopefully it will get resolved when I upgrade to Breezy or when xfce 4.4 comes out (which should be fairly soon, judging by the recent posts on the xfce-devel blog).

I just have one of those odd, yo-yo mode problems. But if anyone is experiencing similar issues, or has suggestions, I'd welcome them.

Ross

---

### Post by charlieg on 2005-08-08
Slowness in Gnome and Xfce indicates a Gtk problem.  What version of Gtk do you have installed?  Have you been experimenting with things like Cairo?

---

### Post by rosslaird on 2005-08-08
I figured it was probably a gtk problem -- but I haven't been doing anything fancy with gtk or cairo or anything else.

As for my gtk versions:

"pkg-config --modversion gtk+-2.0" reports 2.6.4

"pkg-config --modversion gtk+-2.0" reports 1.2.10 (I think this is for gtk 1)

---

