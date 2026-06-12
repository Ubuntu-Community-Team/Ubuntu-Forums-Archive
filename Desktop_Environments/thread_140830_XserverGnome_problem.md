---
title: "Xserver/Gnome problem"
date: 2006-03-07
forum: Desktop Environments
---

### Post by omppa on 2006-03-07
Yesterday i faced kind of strange problem, but i solved it. And then i started to think that what causes this problem which has got some details below:

 /etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "%username%"
/etc/gdm/Xsession: Beginning session setup...
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/masiina:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/masiina:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/masiina:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco

** (gnome-session:9359): WARNING **: Unable to read ICE authority file: /home/%username%/.ICEauthority

Can somebody tell mee that what causes this problem?

-Sami

---

### Post by Koybe on 2006-03-07
Look at the file causing this problem. Look for the rights on it.
```

ls -la /home/%username%/.ICEauthority
```

it sould be set to something like this. 
```
-rw-------  1 %username% %username%  28651 mar  7 06:29 /home/jerome/.ICEauthority
```

If you still got the problem, make a save and erase it. Restart gdm and try it out.

---

