---
title: "Add autorandr before kdm starts"
date: 2012-04-21
forum: Desktop Environments
---

### Post by hydrargyrum on 2012-04-21
I want to add [autorandr]("https://github.com/wertarbyte/autorandr") before kdm starts. Autorandr works well within KDE session, however, in kdm I still have ugly 1024x768 resolution when my external monitor is connected.

I tried adding autorandr --change to /etc/kde4/kdm/Xsetup:

```
#! /bin/sh
# Xsetup - run as root before the login dialog appears

#xconsole -geometry 480x130-0-0 -notify -verbose -fn fixed -exitOnFail -file /dev/xconsole &

/sbin/initctl -q emit login-session-start DISPLAY_MANAGER=kdm

/usr/local/bin/autorandr --change >> /tmp/autorandr
echo "Xsetup finished" >> /tmp/xsetup-finished
```

A debug message in /tmp/xsetup-finished appears correctly. /tmp/autorandr is empty (so it seems autorandr runs without errors).

I also tried to move autorandr --change line before /sbin/initctl -q emit login-session-start DISPLAY_MANAGER=kdm with no effect.

P.S. Of course, autorandr profiles I created under KDE session, are in my home folder, but Xsetup script runs under root, so I created a symlink from my ~/.autorandr to /root/.autorandr.

---

