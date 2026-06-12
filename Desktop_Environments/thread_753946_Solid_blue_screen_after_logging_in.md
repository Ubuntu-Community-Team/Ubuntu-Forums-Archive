---
title: "Solid blue screen after logging in"
date: 2008-04-13
forum: Desktop Environments
---

### Post by Shaydog on 2008-04-13
I'm having an issue with Gnome.  After I log in at the login screen, I get a solid blue screen with just the mouse cursor.  It's not frozen since the mouse cursor moves.  In addition, when I shut down or hit Ctrl + Backspace, I can see my normal desktop appear for a second before the shutdown process starts.

When I hit Ctrl + F1 I get into what looks like should be a command prompt, but it's frozen.

The problem is very similar to the one described here:
[http://ubuntuforums.org/showthread.php?t=242605](http://ubuntuforums.org/showthread.php?t=242605)

Except it's a blue screen and I wasn't doing any sort of upgrading.  I reconfigured Beryl right before shutting down, but that was it.

Any help would be greatly appreciated.

Thanks

---

### Post by Martje_001 on 2008-04-13
Press ALT+F2, wait a few seconds and typ **metacity --replace** and press enter. Does this get your desktop back?

---

### Post by Shaydog on 2008-04-13
Martje_001, that did it.  Thank you very much.  Could you give me some insight into what the problem was and how that command was able to fix the issue?

Thanks again!

---

### Post by Martje_001 on 2008-04-14
Ubuntu tries to enable compiz, but this went wrong. However, compiz did not return an error to Ubuntu, so it didn't disable it.
With the command 'metacity --replace' you enable the default desktop without effects (window manager is called metacity).

---

