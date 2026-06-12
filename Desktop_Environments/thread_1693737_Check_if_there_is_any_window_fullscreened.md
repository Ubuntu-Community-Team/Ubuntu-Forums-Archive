---
title: "Check if there is any window fullscreened"
date: 2011-02-23
forum: Desktop Environments
---

### Post by Neosano on 2011-02-23
I have following configuration: [http://img684.imageshack.us/img684/7065/desktop1004.png](http://img684.imageshack.us/img684/7065/desktop1004.png)

as you can see, I have two monitors, and my panels are located on the right monitor. Left monitor is a little bit smaller than the right one, so I prefer watching films on the right one. But if there's a video fullscreened on the right monitor I can't use my computer because all icons are located on the right monitor. I'd like to move panels to the left monitor(it's easy),
but how can I detect that there's a window fullscreened on it?

---

### Post by Frogs Hair on 2011-02-23
I'm using Ubuntu and the short cut key for full screen is F11 By using the shortcut to move back and forth the difference is easily seen.
 
Not having used dual monitors , I don't know if using such a shortcut would cause both screens to change.

---

### Post by Neosano on 2011-02-23
Uh, I can go back from fullscreen, click what I need, and then fullscreen it again.

I have another problem..
here's another screenshot explaining my problem
[http://img254.imageshack.us/img254/6764/screenshotzt.png](http://img254.imageshack.us/img254/6764/screenshotzt.png)

---

### Post by Frogs Hair on 2011-02-23
I use movie player , that is the default in Ubuntu 10.10 and it has full screen on or off check mark on the edit tab , but again the shortcut is F11.

---

### Post by Neosano on 2011-02-24
> **Frogs Hair said:**
> I use movie player , that is the default in Ubuntu 10.10 and it has full screen on or off check mark on the edit tab , but again the shortcut is F11.
I WANT TO USE FULLSCREEN!!!
I just want my panels to move to another screen.

---

### Post by Frogs Hair on 2011-02-24
Sorry if I misunderstood . The panels are made to appear  on all screens as part of the work space switching function . I use a dock and that also appears on all work spaces . It is not possible to delete the panel on another workspace with the default set up.   I'm guessing this is true for another monitor.

I'm not saying what you want to do is impossible , but  it would require some script writing skills and understanding of how the panels work on each workspace. Many people use TV screens with computer , so there may be something gained by learning how that is done.

I think watching movies was not considered when  workspace switching was developed , but I could be wrong.

---

### Post by Frogs Hair on 2011-02-24
I also looked into Compiz  settings , but what I found indicated that Compiz is not user friendly on Lubuntu . You could explore this further because I'm not aware of a Compiz setting the would produce the desired result .

---

### Post by Neosano on 2011-02-24
I already wrote a script for moving panels, but WHEN should it be executed?
I can make a shortcut for it, but I want it to be executed right when some window got in fullscreen mode.

---

### Post by gobbledigook on 2011-02-24
before you get all scripted up ;) you may want to check the video settings? you can define which monitor is your main monitor (ie with the panel on it) and which is secondary... ie set the left as primary and right as secondary...

sorry i can't give more detail... at work so no reference

---

### Post by Neosano on 2011-02-24
... are you kidding, guys?

Everything works correctly. Panels are placed on the right monitor, video can be played anywhere I want. Just forget about panels and other stuff.....
...
There's a command line tool called xwininfo, it can tell a lot of useless information, but it doesn't tell if window is fullscreen...
wmctrl doesn't really help too.
maybe it's possible to catch window manager event?

---

