---
title: "Help xserver crashes when i log in with a desktop environnement"
date: 2006-02-15
forum: Desktop Environments
---

### Post by Dr. Pariolo on 2006-02-15
Hi all!
I recently installed throught synaptic a package that would let me choose my x server at log in. That sounds me interesting so i dled.

But when i rebooted my pc, wich ever desktop environnement i choosed(GNOME, KDE, XFCE, window maker, enlightment, rat poison, gnome fail safe, etc...(Ive installed 9 of them), i get the following error:
```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "docpariolo"
/etc/gdm/Xsession: Beginning session setup...
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

** (gnome-session:8039): WARNING **: Unable to read ICE authority file: /home/docpariolo/.ICEauthority

```
Ive already tried to open that ICE authority file, via knoppix, and there was only:
```
0000
```in it.
Currently using ubuntu's kernel recovery mode(god bless you recovery mode :D ) and trying to found out how to fix my system. Could somebody help me please?

---

### Post by Dr. Pariolo on 2006-02-15
Things ive tried up to now:
-Re-Install iceauth
-Install KDM
-Reconfigured xorg

Because the problem was from an ICEauth file, i was wondering if by uninstall it, my system would be fixed... But many apps depends on ICEauth! included gdm!
what should I do?

---

### Post by Dr. Pariolo on 2006-02-15
-----------------------------------FIX-----------------------------------
1º)Load failsafe kernel
2º)startx
3º)log on with gdm(If you had autologin enabled, you should normaly be logged on as root)
4º)Open nautilus, locate your ICEauth config ice(personal account, not root!)
Should be(example):
```
/home/docpariolo/.ICEauthority
```
5º)Set it as your personal id account, and not root!
6º)Give it full permissions

You should have something like this:
[IMG]http://img117.imageshack.us/img117/6665/screenshoticeauthorityproperti.png[/IMG]
Restart with normal kernel

enjoy :P

---

