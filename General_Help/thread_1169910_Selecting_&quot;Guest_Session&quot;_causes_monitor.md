---
title: "Selecting &quot;Guest Session&quot; causes monitor to lose input."
date: 2009-05-25
forum: General Help
---

### Post by Buttons840 on 2009-05-25
In the shutdown/restart menu there is the option to start a "Guest session."  I tried selecting it, the screen turn black, and then my monitor reports no input and turns off, yet the computer is clearly still active, evidenced by the periodic HDD access indicator flashing.  By all indications (minus the monitor) the computer is still running.

Any idea what I can do to fix this?  Or any way to remove "Guest session" from this menu.  Otherwise I'm always 1 click away from having to hard reset the computer (aka, pull the plug).

---

### Post by Buttons840 on 2009-05-25
I have an update.  The problem begins when I install the ATI proprietary drivers.

When I switch to a guest session the system appears to lock up.  At first I though the display was simply disabled for some reason, but it now appears that the system is indeed frozen/locked.

Any help is appreciated.

---

### Post by trench.me on 2009-05-26
After you switch to the Guest Session try tty9 [ctrl + alt + F9]. Last week I discovered that an active Guest Session always resides on tty9. Ergo, if you have Guest Session active, the quick mouse-free shortcut between your user session and your GS is as simple as toggling tty7 and tty9. The GS was awesome before I discovered this... now it's even more-so. 

Although this doesn't exactly ***fix*** your problem, it could be a good starting point for discovering what's going on. 

Probably a good idea to check your xorg log too.

Recreate the problem and then examine the last few lines of:

```
cat /var/log/xorg.0.log
```

Check your other logs too, look at the time-stamps to corroborate, and paste any suspicious errors here.

---

