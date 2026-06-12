---
title: "Gnome panel applets keep moving and overlapping"
date: 2011-01-03
forum: Desktop Environments
---

### Post by anypundit on 2011-01-03
In Lucid I don't have many panel applets but they keep rearranging, leading to shutdown difficulty amongst other issues.  The Clock, battery, wifi, sound and email Indicator applets seem to be unaffected, but Diskmounter, the shutdown and user/social networking Indicator icons get moved and/or squished together with each restart.

My volume control icon disappeared this time as well.  The next time I typed my password for elevated privileges, the temporary addition of the key-shaped icon to the notification area fixed my clock applet.

---

### Post by karthick87 on 2011-01-03
Right click the applet and click on **Lock to Panel**.

---

### Post by Pilot824 on 2011-02-03
Im using Ubuntu, however having the same problems EVEN IF I tell it to lock to the panel.

The applets rearrange themselves usually after I restart my computer.

---

### Post by anypundit on 2011-02-03
Indeed, all my icons were locked, but now half of the date and time is covered by a blank space.  It seems to happen every so often after a restart.

---

### Post by anypundit on 2011-02-25
Everything is locked and it's still happening.  Should I submit a bug report at this point?

---

### Post by Scott Deagan on 2012-01-20
I'm using Ubuntu 10.10 on three different computers, and I can confirm that this issue still exists (even if you lock everything to the panel).

I use dual-monitors with my laptop, and the problem seems to be worse on this machine (happens just about every single time).

---

### Post by Frogs Hair on 2012-01-20
You could try resetting the panel the following command .```
gconftool --recursive-unset /apps/panel && killall gnome-panel 
```

---

