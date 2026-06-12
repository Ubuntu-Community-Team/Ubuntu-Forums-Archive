---
title: "xfce bringing blank screes"
date: 2008-06-06
forum: Desktop Environments
---

### Post by gdkeene on 2008-06-06
I am running Ubuntu, but I installed xfce.  Every time I log into an xfce session, it just brings a black screen, but the mouse works.  I then hit <Ctrl><Alt><Backspace> and login again and this time it works fine.  This is repeatable every time.

I re-installed xfce, but it didn't change anything.

Any ideas?

Thanks

---

### Post by unicorn_2003_1 on 2008-06-06
"That error you got states that dbus is not running. XFCE needs dbus to communicate between the various components and applications. Run /etc/init.d/dbus and see if that helps. After running dbus run xfce4-session to start your session." ---quote

the link:[http://ubuntuforums.org/showthread.php?t=355665]("http://ubuntuforums.org/showthread.php?t=355665")

Good luck.

---

