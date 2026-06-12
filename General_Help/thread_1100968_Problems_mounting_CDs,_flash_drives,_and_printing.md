---
title: "Problems mounting CDs, flash drives, and printing"
date: 2009-03-19
forum: General Help
---

### Post by fliksr on 2009-03-19
I've been running Ubuntu on a Dell laptop for two months or so now.  Everything was going well until I installed one of the update packages two weeks ago.  I started having printing issues (told me printer may not be connected) then noticed it wasn't able to mount my flash drives or CDs.

This is the latest error message when trying to access the CD:

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

I've been a Windows guy since 3.1... got sick of the memory hog (Vista) and made the switch.  Was very happy until recently.

So, where do I need to start looking to fix this?

Thanks!

---

### Post by fieroboom on 2009-03-19
Run these commands and copy/paste the output here please.
```
eval dbus-launch

ps aux|grep dbus
```
:D
-Paul

---

### Post by fliksr on 2009-03-19
eval dbus-launch gave me this:

DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-jSfoN9uYfS,guid=d4e17ad6a30ca31496e6527b49c2e87c
DBUS_SESSION_BUS_PID=15584

ps aux|grep dbus gave this:

108       4737  0.0  0.0   3000  1288 ?        Ss   16:55   0:04 /bin/dbus-daemon --system
jeremy   11924  0.0  0.0   3124   672 ?        S    19:32   0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session /usr/bin/seahorse-agent --execute x-session-manager
jeremy   11925  0.0  0.0   3036  1264 ?        Ss   19:32   0:00 //bin/dbus-daemon --fork --print-pid 6 --print-address 9 --session
jeremy   15584  0.0  0.0   2640   492 ?        Ss   20:51   0:00 //bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
jeremy   15721  0.0  0.0   3240   804 pts/0    S+   20:53   0:00 grep dbus

---

### Post by fliksr on 2009-03-20
ttt

anybody?

---

### Post by fliksr on 2009-03-20
[Link]("http://ubuntuforums.org/showthread.php?t=779992")

Whoever came up with the stuff in the above link -THANK YOU.  Seemed to fix every problem with the system.  Let's see if the next update screws anything else up

---

