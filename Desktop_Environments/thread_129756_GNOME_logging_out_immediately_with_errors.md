---
title: "GNOME logging out immediately with errors"
date: 2006-02-14
forum: Desktop Environments
---

### Post by joeljkp on 2006-02-14
I booted up my laptop today (just regularly, nothing different from any other time), and GNOME quit as soon as it started, popping up  a message box saying that it logged out within 10 seconds and that I should be looking for errors.

I rebooted a few times, unplugging all my periphs, network cable, etc., but I get the error every time.

Here's the contents of the file it told me to look at (~/.xsession-errors):

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "joeljkp"
/etc/gdm/Xsession: Beginning session setup...
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/fry:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/fry:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/fry:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco

** (gnome-session:7680): WARNING **: Unable to read ICE authority file: /home/joeljkp/.ICEauthority
```

My .ICEauthority file has a bunch of binary-looking stuff in it, but I don't know if it's anything abnormal.

Can anyone help me?

---

### Post by christhemonkey on 2006-02-14
Need to change the permissions on your .ICEauthority file or just plain remove it.
For some reason it seems to randomly change and give errors!
```
sudo rm .ICEauthority
```
```
sudo chmod 777 .ICEauthority
```

---

### Post by joeljkp on 2006-02-14
Cool, that worked.

Thanks!

---

