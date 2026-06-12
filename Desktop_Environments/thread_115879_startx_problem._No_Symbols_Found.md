---
title: "startx problem. No Symbols Found"
date: 2006-01-11
forum: Desktop Environments
---

### Post by foresight on 2006-01-11
Fresh after installing Ubuntu 5.10 Breezy Badger, I keep getting this error when I try to run X:
```

Skipping "/usr/X11R6/lib/modules/extensions7libGLcore.a:m_debug_clip.o" No symbols found
Skipping "/usr/X11R6/lib/modules/extensions7libGLcore.a:m_debug_norm.o" No symbols found
Skipping "/usr/X11R6/lib/modules/extensions7libGLcore.a:m_debug_xform.o" No symbols found
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o" No symbols found

```
Im trying to install into a HP Pavilion zd8100 laptop.
I've tried to reinstall Ubuntu several times with different boot options but still no go. I also spent some time on #Ubuntu @ irc.freenode.com but none of the tips I got there helped. (but dang those guys are helpfull..so thanks for the effort)
In addition I'm unable to run dpkg-reconfigure -phigh xserver-xorg, 
it just keeps exiting right away saying 
```
xserver-xorg postinst warning: overwriting possibly customised configuration
```
I tried deleting the .conf backups but still wont run.

Im rather new to installation of linux, only thing I've done before is use computers with linux preinstalled, so any help you can give, I'd appreciate it being straightforeward and exact :)

Thanks

---

### Post by foresight on 2006-01-11
UPDATE
I worked it out..it seems it was quite simple, tho no-one knew how.
all it needed was to update the ATI drivers with the fglrx drivers.
It is an ATI radeon X600 Mobile, in case anyone else get a similar problem :)
[https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)
It works and Im happy :)

---

