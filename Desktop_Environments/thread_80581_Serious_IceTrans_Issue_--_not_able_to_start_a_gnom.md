---
title: "Serious IceTrans Issue -- not able to start a gnome session"
date: 2005-10-22
forum: Desktop Environments
---

### Post by tregetour on 2005-10-22
I get the gnome graphical login. Enter my uname & password. And then It tells me that my session lasted less than 10 seconds and spews back to the login screen. The failsafe sessions does the same, only the xterm session works. So I have nothing but the command line. The error it gives is:

_IceTransNoListen: unable to find transport tcp
_IceTransmkdir: ERROR: euid !=0,directory /dev/X will not be created
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, error=13
_IceTransOpen: transport open failed for pts/golem
_IceTransMakeALLCOTSServerListners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/golem
_IceTransMakeALLCOTSServerListners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/golem
_IceTransMakeALLCOTSServerListners: failed to open listener for sco

Any help getting my GNOME back would be very very much appreciated!!

[[p.s. I had to copy the error message my hands so minor discrepencies may have crept in.]]

Thank you in advance again! [I'm stuck on an old windows machine till this gets fixed.]

---

### Post by jasonmartens on 2005-12-08
I am having this exact same problem on a brand-new breezy installation (using amd64 with 64 bit ubuntu).  Here is the .xsession-errors from my system.  

cat .xsession-errors
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "erika"
/etc/gdm/Xsession: Beginning session setup...
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/erikalinux:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/erikalinux:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/erikalinux:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco
SESSION_MANAGER=unix/erikalinux:/tmp/.ICE-unix/7444


I should also note that GDM starts up fine.  After logging in however, I get a blank brown screen with just the mouse on it, and it hangs there forever.   I cannot kill it and go back to the console, I have to press the reset button on the computer to get it to respond again.

---

### Post by balintme on 2005-12-29
Hi, they find out how to solve it; I had the same problem, but with this info I could fix it.

[http://ubuntuforums.org/showthread.php?t=80599&highlight=IceTrans](http://ubuntuforums.org/showthread.php?t=80599&highlight=IceTrans)

---

