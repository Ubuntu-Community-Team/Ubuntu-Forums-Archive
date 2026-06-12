---
title: "can't start x-session"
date: 2005-12-20
forum: General Help
---

### Post by Jefo on 2005-12-20
Just got Unbuntu Breezy, was installing programs and, after some rebooting, could not start x-sessions anymore. Here is the log file (~/.x-session-errors):

/etc/gdm/PreSession/Default: Registering your session with wtmpand utmp
/etc/gdm/PreSeesion/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h  "" -l ":0" "user"
/etc/gdm/Xsession: Beginning session setup...
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0, directory /dev/X will not be created 
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13 
_IceTransOpen: transport open failed for pts/ubuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts 
_IceTransISCOpenServer: protocol is not supported by a ISC connecton
_IceTransOpen: transport open failed for isc/ubuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransISCOpenServer: protocol is not supported by a SCO connecton
_IceTransOpen: transport open failed for sco/ubuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco

** (gnome-session:9055): Warning **: Unable to read ice authoroty file: /home/user/./ICEauthoroty

That's it. I would appreciate any help...

---

### Post by matthewv on 2005-12-20
Maybe you could find the file the log file refers to (/home/user/.ICEauthority) and ensure that you have adequate permissions to access it... Don't know if that will help, just an idea...

---

### Post by Jefo on 2005-12-21
Resolved by removing /home/tomubuntu/.ICEauthority file. I found the solution here:

[http://www.justlinux.com/forum/showthread.php?threadid=138003](http://www.justlinux.com/forum/showthread.php?threadid=138003)

Thanks matthewv.

---

