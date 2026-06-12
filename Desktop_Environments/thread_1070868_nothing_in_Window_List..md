---
title: "nothing in Window List."
date: 2009-02-15
forum: Desktop Environments
---

### Post by bosworthy on 2009-02-15
Hi, 

I don't know what happened to my gnome desktop.  I have a few applications running such as firefox and synaptics, but I don't see anything in the window list.  When I add the window list to the bar at the bottom, the applications briefly appear, then disappear.  What's going on?

I have dual monitor, an external monitor is connected to my laptop.  I created another "panel" and moved it to my laptop's bottom portion, and added the window list, and all my programs shows there.  But soon as I drag the panel down to the area of my second monitor, the applications disappear in the window list.  I believe this is a bug.  I'm using ubuntu 8.04 and it's all updated.

I've googled, and it seems the issue is still not resolved since 2008?
[https://bugs.launchpad.net/ubuntu/+source/libwnck/+bug/260939](https://bugs.launchpad.net/ubuntu/+source/libwnck/+bug/260939)

this is reproducible 100%.  please see attach.  Note the panel on midscreen and bottom.

128MB ATI Xpress 200m video.  HP zv6000 laptop


Thanks.

---

### Post by Captain Starfish on 2009-02-16
Confirmed still an issue in Intrepid Ibex.

This machine was a fresh install, same problem as before.

I put a 2nd Window List on the 2nd monitor, they don't appear there either when the window is entirely on monitor 2.

If I drag that window left a little, so it overlaps back onto monitor 1, its icon appears in the 2nd window list. More than half the window width on the first monitor, the icon jumps across to the window list on the first monitor.

Entirely back on the 2nd monitor? Icon disappears again.

---

