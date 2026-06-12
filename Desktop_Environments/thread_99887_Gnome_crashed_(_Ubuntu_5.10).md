---
title: "Gnome crashed ( Ubuntu 5.10)"
date: 2005-12-06
forum: Desktop Environments
---

### Post by Mr.Hulot on 2005-12-06
Hi all! I recently install ubuntu 5.10 alongside the virus (winXP) and a Fedora core 4 system. Everything went well and for a period of about a month I was working with ubuntu as I was pretty much thinking of dumping fedora for it.(Unfortunately the virus is hard to kill because of a problem with my ipod, but that's another story). So yesterday after some poking around in ubuntu I tried to login in gnome and it just didn't. I get a message that my session lasted less than 10 seconds and an error message that says these: 

[I]/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "mrhulot"
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/ubuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/ubuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/ubuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco

** (gnome-session:7313): WARNING **: Unable to read ICE authority file: /home/mrhulot/.ICEauthority[/I]

I tried to enter with the failsafe option but I still get the same message. The problem is I don't remember exactly what I messed up! I remember installing totem-xine and after seeing a thread here of a similar problem after installing totem, I removed it but I had no change. 
So is there a way to salvage my installation (not to mention the configuration of my non-linux compatible wireless network card) by repairing gnome? A last resort is of course formatting and reinstalling but ... I prefer a more delicate solution if there is one!

Thanks !

---

### Post by Strider420 on 2005-12-07
I had the same problem but found the solution [here](http://www.ubuntuforums.org/showthread.php?t=98738)

---

