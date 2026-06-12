---
title: "X won't start anymore"
date: 2005-11-19
forum: Desktop Environments
---

### Post by patrickfromspain on 2005-11-19
Hi there! I just got the ubuntu 5.10 cds this week, and installed ubuntu to gave it try. I like it a lot, better than suse. Well... nothing has gone wrong until today. I go into Ubuntu, log in, patrick, password and.... A pop up window comes out saying that my session has been shorter than 10 seconds and bla bla I may have a bad installation, or run out of disk space or whatever.

Ok, installation isn't the problem, as I've used ubuntu for a couple of days. Disk space is ok, no problem.

my .xession-errors file shows:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "patrick"
/etc/gdm/Xsession: Beginning session setup...
_IceTransTransNoListen: unable to find transport: tcp
_IceTransPTSOpenServer: Unable to link /dev/pts/0 to /dev/X/ICE.10579
_IceTransOpen: transport open failed for pts/ubuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/ubuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/ubuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco

** (gnome-session:10579): WARNING **: Unable to read ICE authority file: /home/patrick/.ICEauthority

And another thing, if in the login window I try safe mode no way, the happens. I've rebooted and in grup selected safe mode... i goes into text mode and as root. There, I can do startx without a problem. Here I am in ubuntu. Then, I've tried su patrick, password, and startx... nothing. It say my user hasn't the permissions or whatever to launch X. Hope you can help.

See you.

Patrick

---

### Post by angkor on 2005-11-19
Try removing the .ICEauthority file from your /home....it should create a new one and you'll be able to log in again.

Switch to the console at the login screen with Ctrl-Alt-F1. Log in and remove the file. Use Ctrl-Alt-F7 to get back to the login and give it a try.

---

### Post by patrickfromspain on 2005-11-19
First, sorry for posting. I should have done a search before :) 

Thank you for replying. Instead of deleting i changed the permissions of ICEauthority. Now it works... but is the problem fixed? Or will it appear again?

Anyway, thanxs.

---

### Post by angkor on 2005-11-19
I think I read somewhere it could be caused by KDE apps like K3b, but I'm not sure. Now you know how to fix it though. :)

---

