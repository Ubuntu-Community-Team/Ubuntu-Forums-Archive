---
title: "Guest session does not work anymore"
date: 2009-01-07
forum: Desktop Environments
---

### Post by jis on 2009-01-07
I have launched guest session like told in [another thread]("http://ubuntuforums.org/showthread.php?t=967464"), but it does not work anymore: only blank background appears and mouse cursor. Before removing openbox package guest session was an openbox session even if I launched it from Xfce session. How can I get guest session to work?

OS: Xubuntu 8.10 with additional sw source "deb [http://ppa.launchpad.net/xubuntu-dev/ubuntu](http://ppa.launchpad.net/xubuntu-dev/ubuntu) intrepid main"

---

### Post by jis on 2009-01-07
I got away from the blank guest session by pressing Ctrl-Alt-F1 Ctrl-Alt-F7 and typing my password in the screen lock. But I suppose the guest session was not quited properly that way:

> $ mount | grep /tmp/guest-home.
none on /tmp/guest-home.J21824 type tmpfs (rw,mode=700)


---

### Post by jis on 2009-01-11
Guest session works, if I change Default Session from "Run Xclient script" to "Xfce Session" in gdmsetup. (Applications > System > Login Window)

---

