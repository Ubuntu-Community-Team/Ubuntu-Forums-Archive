---
title: "Can workspace switching be initiated automatically?"
date: 2007-12-16
forum: Desktop Environments
---

### Post by Jollyman on 2007-12-16
I am using Ubuntu Gutsy.  I would really like to be able to configure several workspaces and then automatically scroll through them, say every 5 seconds.  My intent is to use this as a type of Master Control, so at a glance I can look and see that everything is OK.  I do not want to have to initate the workspace switch, I would like it to happen automatically if there is no mouse or keyboard activity.  I it possible to do something like this?

---

### Post by catach on 2007-12-17
Interesting question! I suppose you could write a cron job that calls [wmctrl](http://www.sweb.cz/tripie/utils/wmctrl/) (install from Universe). 

However, cron doesn't seem to be designed for tasks activated as often as you want, and wmctrl seems to only work when Visual Effects are set to "None".   

I don't know about the input dectection part.

---

