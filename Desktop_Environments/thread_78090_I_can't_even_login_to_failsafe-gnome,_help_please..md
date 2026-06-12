---
title: "I can't even login to failsafe-gnome, help please."
date: 2005-10-17
forum: Desktop Environments
---

### Post by DrayKO on 2005-10-17
I just did an (too?)extensive upgrade and propably messed a bit so quite possibly all my fault=). Here's what gdm gives(~/.xsession-errrors):

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp $/etc/gdm/Xsession: Beginning session setup...
No profile for user 'user' found
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/ubuntu-4:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/ubuntu-4:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/ubuntu-4:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco

** (gnome-session:9466): WARNING **: Unable to read ICE authority file: /home/u$


What might be the reason for this? Any solutions.

Thanks.

Elmo

---

