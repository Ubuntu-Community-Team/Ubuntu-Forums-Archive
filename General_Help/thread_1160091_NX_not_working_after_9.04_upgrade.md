---
title: "NX not working after 9.04 upgrade"
date: 2009-05-15
forum: General Help
---

### Post by hellz99 on 2009-05-15
Last night I finally upgraded to 9.04, now I can't remote in via nxserver.  The connection actually happens, and I see the desktop for a second and then it closes out.  I've read a few forum threads (which are now closed which is why I'm posting here) that said there was a gnome-panel bug that was causing it, and is now supposedly fixed.  

I'm running gnome-panel 1:2.26.0-0ubuntu7, and tried reverting back to ubuntu4, but after trying:
```
sudo aptitude install gnome-panel=1:2.26.0-0ubuntu4
```
I get:
```
Unable to find a version "1:2.26.0-0ubuntu4" for the package "gnome-panel"
```


I ran tail on the log while trying to remote and I keep getting errors like:
```
dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.36" (uid=1000 pid=3993 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.185" (uid=110 pid=26944 comm="/usr/lib/policykit/polkitd "))
```

Which I'm guessing is the problem. 

Any idea?

---

### Post by hellz99 on 2009-05-15
The way I was able to get it working again was by uninstalling and installing:
nxclient
nxnode
nxserver

I'm not sure if it was the reinstall process that fixed it or was me upgrading the nx files (I have no idea what the prev version I had was).

In case you don't know how to uninstall these....
[LIST=1]
[*]System->Administration->Synaptic Package Manager
[*]type "nx" in the quick search
[*]you'll see the three thing to uninstall, right click and choose uninstall.
[/LIST]
This is assuming you followed something like this [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX) where you add the sources and install from there.  If you did a manual, then you can manually delete it.

---

