---
title: "x11vnc+kdm =&gt; KDE is not starting"
date: 2011-08-25
forum: Desktop Environments
---

### Post by Lord93 on 2011-08-25
I'm trying to install and use VNC on Kubuntu 10.04 headless computer, and KDM is really good working, but after I type login/pass and login to KDE, Xorg is crashing.


My config solution is to install a "xserver-xorg-video-dummy" package and edit Xorg.conf with lines as:
```

Section "Device"
  Driver "dummy"
...
Section "Monitor"
  "ConnectedMonitor" "LCD"
...

```

and my code for /etc/kde4/kdm/Xsetup (to start x11vnc with kdm):
```
/usr/bin/x11vnc -o /var/log/x11vnc.log -display :0 -rfbauth /etc/x11vnc.pass -forever -bg
```


P.S. I found my problem, it's not in KDE/VNC, it's in the user profile somewhere. I've just created a new user and everything is working now.

-------------------------------

So, after I typed login/pass, it crashed with ~/.xsexxion-errors:

```
Xsession: X session started for u at &#1055;&#1090;&#1085; &#1040;&#1074;&#1075; 26 01:58:03 OMSST 2011
Setting IM through im-switch for locale=ru_RU.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
startkde: Starting up...
kdeinit4: preparing to launch /usr/lib/libkdeinit4_klauncher.so
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
kdeinit4: Can not connect to the X Server.
kdeinit4: Might not terminate at end of session.
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kded4.so
kdeinit4: (kded4 /usr/bin/kded4) Pipe closed unexpectedlykdeinit4: Pipe closed unexpectedly: No such file or directory
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kcminit_startup.so
kdeinit4: (kcminit_startup /usr/bin/kcminit_startup) Pipe closed unexpectedlykdeinit4: Pipe closed unexpectedly: No such file or directory

```

Please help me, what I'm doing wrong? :(

P.S. that "xinet.d+x11vnc" that i've seen on google is not working at all. I need access to KDM and KDE both via VNC.

---

