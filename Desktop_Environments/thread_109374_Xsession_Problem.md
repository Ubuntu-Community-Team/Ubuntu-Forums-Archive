---
title: "Xsession Problem"
date: 2005-12-28
forum: Desktop Environments
---

### Post by rado_london on 2005-12-28
Hi
Couple of days ago I installed XFCE. It was fantastic. Then I made it to look like OS X (GTK, Icons). It ran fine for a while. Today I triedd to loging as usual but I got a strange error message(I tried to start both XFCE and GNOME but the result was the same):

```

Your session only lasted less than 10 seconds. If have not 
logged out yourself, this could mean that there is some
 installation problem or that you may be running out of diskspace.
 Try logging in with one of the failsafe sessions to see if you can fix this problem.

~/.xsession-errors file

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default/: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmo -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "rado"
/etc/gdm/Xsession: Begining session startup...
_IceTransTransNoListen: unable to find transport: tcp
IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno= 13
_IceTransOpen: transport open failed for pts/linux
_IceTransMakeAllCOTSServerListeners: failed to open listeners for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for sco/linux:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco


** (gnome-session :8033): WARNING **: Unable to read ICE authority file: /home/rado/.ICEauthority
```

Hope someone can help me because my XFCE and GNOME were perfectly customized and I dont wanna loose any configurations.

Thanks in advance!

---

### Post by art on 2005-12-28
Maybe this will help

[http://www.ubuntulinux.org/support/documentation/faq/helpcenterfaq.2004-10-20.5390262102](http://www.ubuntulinux.org/support/documentation/faq/helpcenterfaq.2004-10-20.5390262102)

---

### Post by rado_london on 2005-12-28
I didnt delete it, but i changed the permissions to 777 and it works like a dream.

Thanks a lot

---

