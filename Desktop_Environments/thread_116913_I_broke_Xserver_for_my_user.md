---
title: "I broke Xserver for my user?"
date: 2006-01-13
forum: Desktop Environments
---

### Post by lukus001 on 2006-01-13
Edit, fixed.

How: went into terminal, logged in as user, then done: "Sudo chown Username:username .ICEauthority"

Reason for problem: I'm guessing it's because i configured xserver-xorg as root as some point.


--------------------------------
original message:
--------------------------------

Basically, recently installed ubuntu on a nicly formated computer, spent ages configuring, downloading and install app and so on.

Now when ever i log in i get some Xserver session error and it kicks me back out to the log in screen.

~/.xsession-errors read:

```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "lukus001"
/etc/gdm/Xsession: Beginning session setup...
_IceTransTransNoListen: unable to find transport: tcp
_IceTransPTSOpenServer: Unable to link /dev/pts/0 to /dev/X/ICE.9503
_IceTransOpen: transport open failed for pts/Verpix:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/Verpix:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/Verpix:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco

** (gnome-session:9503): WARNING **: Unable to read ICE authority file: /home/lukus001/.ICEauthority
```

All gribberish to me of course, 

I'm currently logging into root in recoverymode

pleases help - thanks

---

