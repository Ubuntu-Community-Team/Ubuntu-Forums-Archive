---
title: "Compiz messed up Open Arena"
date: 2007-11-28
forum: Desktop Effects &amp; Customization
---

### Post by jsbarnes1002 on 2007-11-28
I installed Compiz in order to get the fancy desktop animations, etc.  Now, when I run Open Arena the screen is messed up.  Specifically, OA no longer runs in "full screen" but in a window, or it runs full screen but not "stretched".  That's not a problem, but the graphics aren't rendering properly.  Things don't look right, it is too dark, and the text menus are garbled and unreadable.

I am assuming that Compiz has turned on some X-window mode or something, 'cause now when I log in, the cursor goes to an "X" and the screen blacks for a second.

Sorry if I sound frustrated, but I come from a Windows background.  It seems like every time I install something under Ubuntu, it breaks something else.  But I don't want to give up on Ubuntu.

Thanks in advance ...

---

### Post by aashay on 2007-11-28
Kill compiz.
```
killall compiz.real
metacity --replace
```

---

### Post by Eddie Wilson on 2007-11-28
Or you can install the Fusion-icon. That way you can switch out and back in to Compiz  before or after a game. You could even write an automatic script to do that for you. I'm lucky so far. I haven't any problems with playing games while running Compiz-Fusion.
Eddie

---

### Post by jsbarnes1002 on 2007-11-30
Not sure that I got Fusion-Icon installed properly.  There is no icon in my system tray.

Also - I'm a little worried about doing a "killall compiz.real" followed by "metacity --replace".  That seems destructive.

Please advise - I don't want to re-install Ubuntu again.

---

### Post by jsbarnes1002 on 2007-11-30
I figured it out.  I had to turn off "GL Extensions" in OpenArena.

I'm assuming that even though I did a killall compiz.real and metacity --replace that after a reboot, I'm still running compiz.

Please advise.  Thanks.

---

