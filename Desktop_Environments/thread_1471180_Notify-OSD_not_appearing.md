---
title: "Notify-OSD not appearing"
date: 2010-05-03
forum: Desktop Environments
---

### Post by vek on 2010-05-03
No matter what I try, notifications do not appear.  The notify-osd program is running (if I check ps) and nothing ever reports an error.  I just don't see it, or hear it (does it make a sound?)

I think this might be because of my dual screen setup.  I have two screens set up, with the screen on the right lower than the screen on the left so that they match up in real life.

This leaves a dead space above the right hand screen, perhaps its appearing in there?  But I have already used notification-preferences to move it to the left (does that even work?) and still nothing.  What's up?  I rely on notifications to tell me that something's up, since the new "notification area" plugin does not flash and is thus utterly useless on this large screen display (design failure)

---

### Post by vek on 2010-05-04
I can confirm that this is because its a dual monitor.  If I debug the code its unable to find a panel on any of my two monitors (despite both of them having a panel), and then goes into fallback mode, using the entire space of my workspace which includes both monitors. 

It then puts the notification in the empty area above my right hand monitor, in the dead area that I can't see :(

No idea why the call to get the panel stuff is failing but it is.  GDB doesn't lie :)

Edit:  But is in launchpad [https://bugs.launchpad.net/notify-osd/+bug/475373](https://bugs.launchpad.net/notify-osd/+bug/475373)

---

