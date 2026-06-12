---
title: "My server is dead!?!?!?"
date: 2005-12-06
forum: Desktop Environments
---

### Post by Alex^77 on 2005-12-06
Hello friends...

I have restasted my server after 30 days because I had a problem with a processor fan...

So, when I return to login in Gnome I have recived a warning...

The warning say that I have an installation problem and add this dump:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "alessandro"
/etc/gdm/Xsession: Beginning session setup...
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/Server:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/Server:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/Server:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco

** (gnome-session:8299): WARNING **: Unable to read ICE authority file: /home/alessandro/.ICEauthority

Can someone help me??

---

