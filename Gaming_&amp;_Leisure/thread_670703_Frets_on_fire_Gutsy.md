---
title: "Frets on fire Gutsy"
date: 2008-01-17
forum: Gaming &amp; Leisure
---

### Post by me208 on 2008-01-17
I am trying to play frets on fire on my fresh install of Gutsy gibbon (x86) The first time I started it up it worked fine, but now after I launch it my screen goes black for a second of two then it goes back to my desktop zoomed in (on the top left corner) and my mouse doesn't work. 
Below are images of before I launch and after I launch

(before)
[img]http://img89.imageshack.us/img89/2257/screenshotjy0.png[/img]

(after)
[img]http://img230.imageshack.us/img230/8383/newei2.png[/img]

---

### Post by 900donuts on 2008-01-17
are the 3d desktop effects on or off?
if they're on turn them off

---

### Post by DoktorSeven on 2008-01-17
The zoomed in and frozen mouse thing happens when a fullscreen game crashes and leaves the desktop in a different state and the mouse in "hidden" mode (not visible during gameplay).  I can get the desktop back by running 
```
xrandr -s 0
```
or sometimes it requires
```
xrandr -s 1 && xrandr -s 0
```
but to get the mouse back I have to run something (from a terminal or the run dialog **alt-F2**) that unhides the mouse on normal exit, like a game (e.g. rerunning FoF and having it exit normally).  I've found no direct way to do it, though I suppose it's possible to write a program that would do that.

Anyway, I've found that FoF from the repos is horribly slow and the newest version downloadable crashes a lot.  The one that works beautifully for me is the downloadable version 1.2.451 from its [Sourceforge project page](http://sourceforge.net/projects/fretsonfire).

Hope that helps someone.

---

### Post by rudihawk on 2008-01-18
Thanks for the link :)

---

