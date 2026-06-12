---
title: "Set Up Printer"
date: 2009-03-30
forum: Desktop Environments
---

### Post by MadMax2 on 2009-03-30
I'm setting up my HP deskjet, trying to fix some bugs:

1. Checking for dependency: dbus - Message bus system...

error: NOT FOUND! 
[Fixinig dbus Session in xubuntu 8.04 (hardy) 
Some Applications in (x)ubuntu 8.04 complain about missing dbus daemons. Examples are banshee (which displays a nice message, that explains that the dbus is missing) and f-spot (which simply displays a crash dialog).
If you check your processlist (open Terminal, ps -ef|grep dbus) you will find that dbus is running. There is also a dbus-daemon for your user. So what's going on? All applications are missing an environment variable, that tells them where to find your dbus session. So check that this variable is set. Open up a terminal
user@host:~$ echo $DBUS_SESSION_BUS_ADDRESS
unix:abstract=/tmp/dbus-d8Y6rD59C9,guid=9287ee59f3cbd13ded28b096482fd50c
If you don't get any output it's missing!
[COLOR="Blue"]put the following in /etc/X11/Xsession.d/10-dbus[/COLOR] restart the xserver and everything should be fine
#!/bin/bash
if test -z "$DBUS_SESSION_BUS_ADDRESS" ; then
*** # no dbus? launch one!
*** eval `/usr/bin/dbus-launch --sh-syntax --exit-with-session`
fi]

I don't get the blue step (bad command)

Also
hpaio' in '/etc/sane.d/dll.conf'...

error: Not found. SANE backend 'hpaio' NOT properly setup (needs to be added to /etc/sane.d/dll.conf).


Thanks

---

### Post by MadMax2 on 2009-03-31
My question is 
How do I "put the following in" /etc/X11/Xsession.d/10-dbus
ie where/how?
bash: /etc/X11/Xsession.d/10-dbus: No such file or directory
 and

Also
hpaio' in '/etc/sane.d/dll.conf'...

---

