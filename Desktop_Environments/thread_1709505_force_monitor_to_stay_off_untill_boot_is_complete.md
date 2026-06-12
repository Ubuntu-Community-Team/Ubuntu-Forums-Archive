---
title: "force monitor to stay off untill boot is complete"
date: 2011-03-18
forum: Desktop Environments
---

### Post by shaded2 on 2011-03-18
This may be a strange request. 

I would like to have the monitor say off during boot up until my everything loads including my firefox browser.  This it turns on. 

Is there a way to achieve this?

---

### Post by Krytarik on 2011-03-19
I really don't believe that this is possible, sorry.

But funny idea though! ;-)

EDIT: Thinking of it, there *may* be a way, where you
- turn off the boot splash
- run a "xrandr" command through GDM's startup script to turn the output off
- set a "xrandr" command as "Startup Application" with a sufficient delay to turn the output on again
But it may well be that the screen flickers several times during this.

---

