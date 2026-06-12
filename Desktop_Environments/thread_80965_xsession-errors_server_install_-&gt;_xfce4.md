---
title: "xsession-errors: server install -&gt; xfce4"
date: 2005-10-23
forum: Desktop Environments
---

### Post by jasoncof on 2005-10-23
Greetings,

I installed Ubuntu using the server method. I then installed Xfce4 and created an .xsession file that looks like this:

```

# include .bash_profile if exists
if [ -f ~/.bash_profile ]; then
    . ~/.bash_profile
fi

exec startxfce

```

I'm trying to decipher and fix the errors in the corresponding .xsession-errors file and I'm having a difficult time understanding and fixing them. This is the contents of my .xsession-errors right after I login using gdm:

```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h
 "" -l ":0" "jason"
/etc/gdm/Xsession: Beginning session setup...
/usr/bin/startxfce4: X server already running on display :0
_IceTransTransNoListen: unable to find transport: tcp
_IceTransPTSOpenServer: Unable to link /dev/pts/0 to /dev/X/ICE.5526
_IceTransOpen: transport open failed for pts/goloka:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/goloka:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/goloka:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco

** (xfwm4:5532): WARNING **: The display does not support the XComposite extension.

** (xfwm4:5532): WARNING **: Compositing manager disabled.
xscreensaver: 12:00:22: 0: unrecognised ClientMessage "_GTK_LOAD_ICONTHEMES" received
xscreensaver: 12:00:22: 0: for window 0x400001 (xscreensaver)
env: firefox-bin: No such file or directory

```

Any help you can give would be much appreciated.

Thank you!

- Jason

---

