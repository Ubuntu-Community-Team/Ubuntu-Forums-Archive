---
title: "Dead Desktop Space!"
date: 2011-10-12
forum: Desktop Environments
---

### Post by mxndrwgrdnr on 2011-10-12
See attached screen shot. After opening a menu in gimp, the pixels where the menu was never refreshed, even after I closed both the menu and gimp. I'm sure a restart/new session would fix the problem, but I'd like to know how/if I can solve the issue without having to do all that.
thanks
Max

---

### Post by Copper Bezel on 2011-10-12
I've had this happen once before as well, so if you haven't fixed it yet, try running compiz --replace. I think that should fix it and just jumble your windows around a little without having to restart your session.

Edit: For me, it was one time that I suspended with a menu open. It's never happened before or since, but I still have a knee-jerk reaction not to suspend with a menu open. Like avoiding stepping on black tiles on checkered floors. Nervy.

Strangely, suspending and resuming again didn't fix it, either, even though everything is redrawn in that process. And if you notice, it's treated like it's really still there; switch to Expo, and you'll see a little blank menu on each workspace.

Nice backdrop, by the way! = D

---

### Post by mxndrwgrdnr on 2011-10-12
no dice. ran compiz --replace, windows got jumbled and look the same as before, dead space included.

---

### Post by mxndrwgrdnr on 2011-10-12
looks like the compiz --replace didn't totally finish (i.e. there was still a blinking cursor) and i killed it and then everything went haywire. couldn't access any windows or menus or anything, fortunately i was able to access the menu to do a clean reboot. and duh, gray area is now gone. now i'll never know what happened...

---

### Post by Copper Bezel on 2011-10-12
Sorry. = (  I really was curious, too!

Fair to say that something was there that Compiz was rendering. It's crazy - when it happened to me, since I have transparent menus, the box itself was transparent. = ) I don't know where it gets stuck, though - apparently somewhere further down the stack than Compiz, but if it was still being drawn by the application, wouldn't the process need to be running? (Running wmctrl -l was no help, either.)

---

### Post by LinuxFan999 on 2011-10-12
Which version of Ubuntu are you using?

---

### Post by Copper Bezel on 2011-10-12
Looks like 11.04.

---

