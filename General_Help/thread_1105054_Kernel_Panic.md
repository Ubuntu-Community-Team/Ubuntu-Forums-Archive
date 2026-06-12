---
title: "Kernel Panic"
date: 2009-03-24
forum: General Help
---

### Post by MacAnthony on 2009-03-24
The power went out last night and this morning my son's xubuntu machine was booting to a BusyBox session. The line prior was a couple of mounting errors

[PHP]
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.
[/PHP]

After exiting the BusyBox session, I get:

[PHP]
/init: line 231: cannot open /root/dev/console: no such file
[  636.653596] Kernel panic - not syncing: Attempted to kill init!
[/PHP]

I'm going to boot from the install cd and try and check the filesystem, but any other suggestions would be greatly appreciated.

---

### Post by MacAnthony on 2009-03-24
I ran fsck (it didn't fix any errors) and had to shut it down since I had to do something else. When I started it back up, it worked again. not sure what fixed it.

---

