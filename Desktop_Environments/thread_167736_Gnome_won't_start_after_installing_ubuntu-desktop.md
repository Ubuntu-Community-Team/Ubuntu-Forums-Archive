---
title: "Gnome won't start after installing ubuntu-desktop"
date: 2006-04-29
forum: Desktop Environments
---

### Post by beewer on 2006-04-29
Hi. 

I have kubuntu 5.10 box and I installed ubuntu-desktop with command:
apt-get install ubuntu-desktop

In configuration phase I was asked if kdm or gdm should be default. I chose gdm.

Now if I try to start gnome session from login screen, login just stalls just after I have entered my username and password. Screen stays brown.

There seems to .xsession-errors file in my home directory.
It contains following text:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "poikarai"
/etc/gdm/Xsession: Beginning session setup...
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/topaz:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/topaz:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/topaz:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco
SESSION_MANAGER=unix/topaz:/tmp/.ICE-unix/8991

Is this possibly related to this error?

I tried chmod 777 .ICEauthority in my home folder. I also tried removing all .g* files from my home folder but it didn't help.

edit: strange thing happened, I just played around and installed xubuntu-desktop
apt-get install xubuntu-desktop
After logging once to xfce I can login to gnome also! But after reboot gnome won't work until I login to xcfe again.

I also noted that even though I can use this trick to start gnome, applications in gnome start very slowly. Sometimes they don't appear at all.

And some applications seem to start quicker than others. For example firefox opens immediately but for example gnome log out dialog seems to take ages to start.

And if I try to start another login without logout I get error message Cannot connect to xserver session (or something like that).

Please can some one help? What should I do to fix this?

---

### Post by aysiu on 2006-04-29
What should you do to fix this? Create a new user.

Log into XFCE. Then log into Gnome. Go to System > Administration > Users and Groups and create a new user that belongs to the same groups as your old user. Then, slowly--bit by bit--copy over your important configuration files from the old user.

---

### Post by beewer on 2006-04-29
Hi. 

Thanks for the tip. I created new user from KDE User Manager and tried to login but same problems persists. Gnome login stalls.

---

### Post by beewer on 2006-05-01
Hi. 

Can anyone help me please?

I really would like to get ubuntu-desktop working on my computer.

If there is a known bug do you know in which component it is related to?

-b

---

### Post by kushin77 on 2007-06-04
I have the same problem. i tried to user another desktop and when i try to log into the computer it allowes me to put my username and password, it looks as thou it will log in and then goes back to the logon screen. the only way i was able to get into my machine is through another terminal either remote or when i push ctrl-alt-F1 or any other F key. 

ubuntu desktop 6.06:(

---

