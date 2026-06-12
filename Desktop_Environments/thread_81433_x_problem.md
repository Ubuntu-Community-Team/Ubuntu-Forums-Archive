---
title: "x problem"
date: 2005-10-24
forum: Desktop Environments
---

### Post by buildid on 2005-10-24
with breezy and hoary i have face this problem for the second time and would like to ask if what i did , is oke.

i have a dual boot with xp home and breezy , normal working no problem at al till last night.

i could not log into gnome , i saw a message like :

x could not read or execute :
./ICEauthority 

try to use save mode to resolve this problem...

i have installed the aplication mc , and saw that al the rights for this file belongs to the root .

i change this to users also and now i was able to login to gnome for normal use 

so for now this is working, but i was wondering , why does this happens to me for the second time , two differen t versions , and what i did is that oke ?

thank you ..

---

### Post by Xian on 2005-10-25
Sometimes happens when X crashes. Or if you power-off your system without properly logging out & shutting down. There are other reasons but most have to do with X not being turned off correcty by the system.

---

### Post by buildid on 2005-10-25
thank you..

---

### Post by buildid on 2005-10-26
still happens........
this is the error message:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "buildid"
/etc/gdm/Xsession: Beginning session setup...
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/Breezy:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/Breezy:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/Breezy:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco
SESSION_MANAGER=unix/Breezy:/tmp/.ICE-unix/9680

---

### Post by psychicdragon on 2005-10-26
I had this problem once myself. It's probably caused by running some application as root but I have no idea what. Maybe someone more knowledgable has an answer.

To correct the problem, while in your home directory:
```
sudo chown **username**:**username** .ICEauthority
```
But it may just happen again if you don't know what causes it in the first place.

---

### Post by Jonne on 2005-10-26
I had that happen too. And what you posted works. I think it was an update that caused that.

---

### Post by buildid on 2005-10-26
oke ill wait and post again if this works, thank you ....

---

### Post by buildid on 2005-10-27
seems to work so far, thank you

---

### Post by buildid on 2005-10-27
it looks like i have 2 kde aplications installed , and those 2 are changing the rights of ./ICEauthority .

-k3b
-kavi2svcd

have test this twice .............

---

