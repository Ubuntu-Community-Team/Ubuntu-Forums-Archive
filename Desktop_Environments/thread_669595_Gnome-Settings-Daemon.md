---
title: "Gnome-Settings-Daemon"
date: 2008-01-16
forum: Desktop Environments
---

### Post by hibajugala on 2008-01-16
Ok, every time i start up ubuntu studio 7.10 on my vmware to test it, it gives me an error saying "unable to start the gnome-settings-daemon" and my themes and effects dont work. This didnt happen before, but lately it has begun giving me this error.


help would be appreciated :)

---

### Post by koenbeek on 2008-01-16
that's probably linked to the following bug [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/146946](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/146946)

a lot of people seem to have this issue

suggested workaround are :
add gnome-session-daemon to session startup
or
install dbus-X11


there is also a thread on the forums about this : [http://ubuntuforums.org/showthread.php?t=587410](http://ubuntuforums.org/showthread.php?t=587410)
and a suggested workaround and gnome bug in the following message : [http://ubuntuforums.org/showpost.php?p=3776732&postcount=15](http://ubuntuforums.org/showpost.php?p=3776732&postcount=15)

---

### Post by hibajugala on 2008-01-16
thnx :) ill make sure to try these suggestions out

---

