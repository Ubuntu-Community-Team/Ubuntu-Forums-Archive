---
title: "X broken"
date: 2009-06-23
forum: General Help
---

### Post by t0p on 2009-06-23
An unclean shutdown on my ext2 filesystem appears to have broken X, and I don't know how to fix it,

Running 'xfix' in recovery produced output

```
cp: cannot create regular file `/etc/X11/xorg.conf.20090623064050': Read-only file system
```

I tried the command

```
sudo dpkg-reconfigure xserver-xorg
```

which produced same output:

```
cp: cannot create regular file `/etc/X11/xorg.conf.20090623064050': Read-only file system
```

I'm flying blind on this.  Really could do with some instruction please!

I'm on another machine here.  I can't copy-and-paste from the damaged machine, I have to type in by hand any output from it, so please be gentle when asking me to post error messages etc!

**EDIT:**  The last time I was using this machine (it's an Eee Pc 701), I did

```
sudo modprobe p4-clockmod
```

to enable overclocking.  I don't think that's got anything to do with it, because after the modprobe command I rebooted, and everything was working fine.  But I thought I'd mention it.

Something else I forgot to mention: when it all went crazy, what happened is, I booted the machine, logged in, the desktop background image appeared then went distorted like a TV with real bad interference.  I couldn't do anything to change this, nothing was working, so I switched off the machine by the power switch.  I rebooted, and that's when I got all the stuff about unclean shutdown and screwed filesystem.

---

