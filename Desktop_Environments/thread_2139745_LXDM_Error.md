---
title: "LXDM Error"
date: 2013-04-27
forum: Desktop Environments
---

### Post by wolfgentleman on 2013-04-27
I installed LXDM. I could not get it to run it as the default display manager (yes, I had /usr/sbin/lxdm in /etc/X11/default-display-manager), I had to login and run it from tty. I managed to fix that by adding lxdm before exit 0 in rc.local, now my only problem is after I log in through lxdm it tries to use lightdm-xsession. I don't have and never have installed lightdm or lightdm-xsession or whatever package it is looking for, so when it can't find it, it says it can't find it and its falling back to default session and I have to click ok to continue. So its just a mild irritation, but still. Here is the exact message it gives me:  > Xsession: unable to launch "lightdm-xsession" xsession --- "lightdm-xsession" not found; falling back to default session.  Any ideas?

---

### Post by ibjsb4 on 2013-04-29
I don't know if this will do any good in your case or not, but ..

```
sudo dpkg-reconfigure lxdm
```

---

### Post by wolfgentleman on 2013-05-07
> **ibjsb4 said:**
> I don't know if this will do any good in your case or not, but ..

```
sudo dpkg-reconfigure lxdm
```

It didn't... just an error:
insserv: warning: script 'lxdm' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `lxdm'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `lxdm'

---

### Post by wolfgentleman on 2013-05-20
bump

---

