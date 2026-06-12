---
title: "xfconfd not started"
date: 2011-06-04
forum: Desktop Environments
---

### Post by sadrak on 2011-06-04
xfconfd will not start when gdm is invoked first within bootprocess.

When i then login & logout, gdm restarts and xfconfd is there! Restarting gdm from tty1 will also to the trick.

xfconfd is important for some features: FN-Shortcuts for brightness now works, restart & shutdown from logged in user works, ...

How can i fix that? grep -ri xfconf /var/log find only installtionprotocols :-/  Using xdm change nothing (same behavior).

I am not able to start that manual / save to session ... did not know the command :-(

---

### Post by ankspo71 on 2011-06-04
Hi,
After some digging around, I found out I can attempt to start xfconfd by pasting this into the terminal and then press enter:
```
/usr/lib/xfce4/xfconf/xfconfd
```
Being that it is in the libraries system folder, it does not have it's own short command to start it.

The xfconfd daemon probably can't communicate with dbus on startup, or it times out too fast or something. I wouldn't know how to fix this (other people might though), but if running '/usr/lib/xfce4/xfconf/xfconfd' in the terminal works, then I'm sure you could have xfconfd automatically run on startup by creating an entry for it at Applications Menu > Settings > Settings Manager > Session and Startup > Application Autostart. 

Click Add: 
then enter the following:
Name: xfconfd
Command: sh /usr/lib/xfce4/xfconf/xfconfd 
(or similar)

While you are there, make sure none of the services are disabled in Application Autostart window too (such as xfce settings helper). 

In case you need it, the service file for xfconfd is located at /usr/share/dbus-1/services/org.xfce.Xfconf.service and if you need to make changes to the settings of xfconf, you can use the command 'xfconf-query' and use 'xfconf-query --help' for more information.

The resource I found:
[http://www.examplenow.com/package/xfconf/](http://www.examplenow.com/package/xfconf/)

Hope this helps, or at least gives you a point in the right direction.

---

### Post by sadrak on 2011-06-05
thanks ankspo71, now i see, that the problem did not come from missing xfconfd :-/

i make a diff of all processes. After gdm started, i go to tty1 and saved "ps aufx > start1", then i go back to tty7 and hit ALT-PRINT-K, so gdm restarts (and then all works), go back to tty1 and saved "ps auxf > start2" ... after cutting pid & co off i analyzed the diff and only one row has important differences:

```

      \_ /usr/bin/X :0 -nr -verbose -auth /var/run/gdm/auth-for-gdm-biVLVx/database -nolisten tcp vt7
VS
      \_ /usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-o9UvBo/database -nolisten tcp

```

from X --help:
```

vtXX                   use the specified VT number
-br                    create root window with black background
-nr                    (Ubuntu-specific) Synonym for -background none

```

OK, so where can i change this starting behavior to test that?

---

