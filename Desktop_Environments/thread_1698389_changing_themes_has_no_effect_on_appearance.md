---
title: "changing themes has no effect on appearance"
date: 2011-03-02
forum: Desktop Environments
---

### Post by LonelyStar on 2011-03-02
Hi,

I am on 64 Bit ubuntu 10.10.

After an update, the appearance of my desktop ignores the theme. When I change the Appearance preference, I can change the window border but the look of the buttons _only_ changes the in the appearance preference window, not in any other window.

What could this be?
Thanks!
Nathan

---

### Post by Frogs Hair on 2011-03-02
Hi ,

Could you post a screen-shot so I can see if this is related to another thread that may have a solution . It may or may not be the same issue .

---

### Post by LonelyStar on 2011-03-02
Hey,

I attached a screenshot. I found out more about the problem. It has to do with gnome-settings-daemon not running.
I can fix it with 
```

killall -9 gnome-session-daemon && gnome-session-daemon

```
but it is only fixed until next restart. is there a permanent fix?

Thanks!
Nathan

---

### Post by solskenetisak on 2011-03-02
Hi!

I have the same problem, running Ubuntu 10.10, 32-bit.
It happened after an update, as with Nathan.

However, for me, the top- & bottom panels were only altered for a couple of seconds, then reverted back to their normal state.

Attaching a screenshot, aswell.

And the gnome-sessions-daemon-command didn't do the trick for me.
However: **Killing nautilus and restarting it did**.

---

### Post by Copper Bezel on 2011-03-02
This is related to the "Gnome Reverts to Default Theme" megathread in this forum. The workaround right now is to put 

gnome-settings-daemon && killall nautilus

as a startup application. Something is killing the settings daemon on startup, and it's doing it before Nautilus loads. Nautilus has to be restarted to accept the new settings. (This has always been the case; changing icon themes never affects Nautilus until you restart it.)

---

