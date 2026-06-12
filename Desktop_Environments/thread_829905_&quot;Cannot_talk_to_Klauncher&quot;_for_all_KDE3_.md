---
title: "&quot;Cannot talk to Klauncher&quot; for all KDE3 apps"
date: 2008-06-15
forum: Desktop Environments
---

### Post by ProbablyX on 2008-06-15
Hello,

I've been running KDE4.1 for 24h or something now and it's great. However something weird has happened, as of today (Ive tried logging in and out etc) when I launch a KDE3 app like amarok I get a message saying "Cannot talk to Klauncher". After that the app starts but instead of having its icon in the taskbar it appears as a floating window on my desktop, like a plasmoid =/

I read somewhere this is caused by kdeinit not being started, but that was when this occurs under KDE3.
If I try to start kdeinit wont it get in conflict with its KDE4 sister? (As KDE4 apps work nice, same for Gtk apps like Firefox)

Is anyone else getting this?
Thanks!

---

### Post by ProbablyX on 2008-06-15
OK, really weird...
But if anyone else is having the same issues they went away for me after:
1. logout, login, logout, login
2. reboot 2 times
3. KDE is still doing the same, but now Konqueror is slow too and other apps are lagging as well
4. Get annoyed and reboot again
5. Now its working

---

### Post by p_quarles on 2008-06-15
Yeah, this is a persistent problem with KDE3. Normally, it only happens to me after the X server has been restarted during a session. Rebooting will fix it, but that's highly unnecessary. I have been able to fix it by simply running:
```
killall dcopserver
```
and then restarting the session.

---

### Post by bobdobbs on 2009-01-15
Killing dcopserver worked for me.
Thanks.

Any idea why this happens and why this solution worked?

---

