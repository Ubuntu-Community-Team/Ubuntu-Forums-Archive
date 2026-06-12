---
title: "Can't get GNOME to run"
date: 2005-10-15
forum: Desktop Environments
---

### Post by migueljacq on 2005-10-15
Hi all,

I just installed Breezy Badger and upon logging in, Gnome doesn't seem to want to work. From upgrading from Hoary, I kept my home directory under my account (miguel), and I was running openbox at the time instead of Gnome. I don't have openbox any more which is fine, but how do I get Gnome to start up? I selected 'Gnome' from the sessions at login but no luck. I also ran failsafe Gnome, and this worked, no problems. 
Any help much appreciated.

Miguel

I also got this message when logging in:

Your $HOME/.dmrc file has incorrect permissions and is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions.

I followed the instructions and still get the error....

---

### Post by coldwater on 2005-12-02
i seem to have the same problem. i was trying to replace metacity with openbox with the
```
 openbox --replace 
```

later i switched back to metacity with
```
 openbox --replace 
```

but i messed up somewhere. now when i start gnome it doesn't start up anything, no desktop, no panels, just an empty screen. mouse is there, but there's not much i can do. when i log in using openbox, i get the small openbox menu when i right-click on the desktop, but still there are no panels, or my wallpaper, or rather anything. i can login using gnome-failsafe, and it's ok, has everything i need, except my start-up programs.  and it won't save my session.

i guess i should check my startup list, but don't know where to find it :(

so, where is the file that holds the list of my startup programs? or, is there something else i should do?

please help.

--
don't read anything you believe.

---

### Post by migueljacq on 2005-12-02
Don't know if it's the same problem. I read around the forum and eventually changed the permissions of the home folder. 

sudo chmod 700 /home/(username)

Not sure if it will fix your problem! but anything is worth a shot.

Miguel

---

### Post by coldwater on 2005-12-02
unfortunately, that's not it. i skimmed through files in my home folder, but i don't know what to look for. i did found .xsession-errors though, and now it looks like this:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "coldwater"
/etc/gdm/Xsession: Beginning session setup...
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/spiff:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/spiff:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/spiff:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco
SESSION_MANAGER=unix/spiff:/tmp/.ICE-unix/12872



a few logins before it contained quite a lot of openbox errors, but i didn't write 'em down, and now they're gone. it said something like 

"couldn't open /home/coldwater/.local/share/openbox/1133556821-12095-56555184.obs"

but it didn't say why.

please help, i'm not to keen to reinstall the whole thing, and i know that there's gotta be a way to restore my default session.

---

### Post by teaker1s on 2005-12-02
what about installing kubuntu-desktop with apt-get then remove gnome completely and any related folders in your home folder then reinstall gnome-thats how I fixed mine when I killed it

---

### Post by coldwater on 2005-12-02
thanks, sounds like a plan to me :)

but tell me, which are the related folders i can erase safely? yes i can guess, i'm just trying to be careful :)

---

### Post by stiiixy on 2005-12-17
[QUOTE=coldwater]unfortunately, that's not it. i skimmed through files in my home folder, but i don't know what to look for. i did found .xsession-errors though, and now it looks like this:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "coldwater"
/etc/gdm/Xsession: Beginning session setup...
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/spiff:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/spiff:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/spiff:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco
SESSION_MANAGER=unix/spiff:/tmp/.ICE-unix/12872



a few logins before it contained quite a lot of openbox errors, but i didn't write 'em down, and now they're gone. it said something like 

"couldn't open /home/coldwater/.local/share/openbox/1133556821-12095-56555184.obs"

but it didn't say why.

please help, i'm not to keen to reinstall the whole thing, and i know that there's gotta be a way to restore my default session.[/QUOTE]


I have this error to, now. I'm not using openbox or anything. Just happened on a restart. How can I fix? Any idea's?

---

