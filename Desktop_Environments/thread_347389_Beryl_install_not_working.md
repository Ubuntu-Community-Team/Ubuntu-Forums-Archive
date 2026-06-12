---
title: "Beryl install not working"
date: 2007-01-27
forum: Desktop Environments
---

### Post by dignus on 2007-01-27
Morning all,

I was just trying to get Beryl to work, followed this howto: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FBeryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FBeryl_.28ATI.29)

All seems well, but when I try to login with the session just created, the following error appears in ~/.xsession-errors:
```

/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "dignus2"
/etc/gdm/Xsession: Beginning session setup...
_XSERVTransSocketUNIXCreateListener: ...SocketCreateListener() failed
_XSERVTransMakeAllCOTSServerListeners: server already running

Fatal server error:
Cannot establish any listening sockets - Make sure an X server isn't already running

(gnome-session:7724): Gtk-WARNING **: cannot open display
```: 

UPDATE:

I found this in my Xorg.0.log:
```
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering
```


Any suggestions?

---

