---
title: "Minimal X windows"
date: 2007-11-14
forum: Desktop Environments
---

### Post by projectshave on 2007-11-14
I'm running Xubuntu in VMware and running apps remotely using X, VNC or X-Win32 (depending on which remote machine I'm using). This all works fine so far. I'd like to reduce memory consumption in Xubuntu by turning off the desktop and other graphical features I don't use. How can I change runlevel 2 to be a minimal X server sufficient to run terminals and Emacs remotely? I'd like runlevel 3 to be the standard Xubuntu desktop when I need it. 

Thanks.

---

### Post by lavajumper on 2007-11-15
To avoid possibly confusing upgrades, I would suggest customizing runlevel 3 and making it your default.

To change the default runlevel, edit the /etc/inittab file changing

```

# The default runlevel.
id:2:initdefault:

```

to
```

# The default runlevel.
id:3:initdefault:

```

The startup processes are in /etc/rc2.d and /etc/rc3.d respectively.  Also, /etc/rcS.d contains startups common to all runlevels (adjust with extream caution).

As far as a 'minimal' X session, I've never looked that closely at the startup....I would start by digging around in /etc/X11 and also looking at the man page for nautilus.

Another trick I've used to thin out the RAM footprint is to identify and unload kernel modules which I don't use. 'lsmod' and 'modprobe' man pages will help there. 

If you're new to startup procedures, study up first. They can hose your machine if done wrong.

Hope it helps.

---

### Post by bingoUV on 2007-11-15
What?
use twm(light) instead of xfce (heavy). 

How?
Open ~/.xinitrc. Write twm in it. exit. Once you manage to boot into runlevel 3 by the earlier post's suggestion, login and do xinit instead of startx. Welcome to twm.

---

### Post by lavajumper on 2007-11-16
:oops:
WOW, I'm trying to get this egg off my face. I just checked my gutsy machine and I can't find inittab anywhere. Looks like this distro is going to send me back to school!

This is a great thread to work with upstart, the new method.

[http://ubuntuforums.org/showthread.php?t=278725](http://ubuntuforums.org/showthread.php?t=278725)

Does anyone know if Linux still uses a kernel!?

---

