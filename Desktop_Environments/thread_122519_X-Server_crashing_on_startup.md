---
title: "X-Server crashing on startup"
date: 2006-01-27
forum: Desktop Environments
---

### Post by BetaguyGZT on 2006-01-27
Here's the problem. Hope someone can help me.

I installed all updates, then Kubuntu-Desktop in APT, then used Automatix to install the rest of what I wanted. I rebooted once, everything was fine. I fire up KDE, set up Kopete, install a couple of fonts from my backup drive and use it for about an hour. I go to restart again, and after the initial boot-up process and module loading, at the point which GDM *should* load, X is spitting errors at me. I'll have to modify this post to say exactly what it is read, but after the errors I at least have a command prompt so I'm pretty sure I can fix it when pointed in the right direction. Anyway, the X Server diagnostic wasn't very informative. All it gave me was system information.

I *have* tried starting GDM and KDM manually (as SU), nothing.

I *have not* tried reinstalling my video driver yet using APT, or anything else meaningful. I didn't want to potentially make the problem worse if I don't know exactly what I'm doing.

Any help would be appreciated.

---

### Post by dcast on 2006-01-27
try "sudo dpkg-reconfigure xserver-xorg" that will allow you to reconfigure through a wizard.

---

### Post by BetaguyGZT on 2006-01-27
Cool. I'll try that. Thanks. :)

---

### Post by BetaguyGZT on 2006-01-27
Another problem has popped up. I can't access ANYTHING now. This is the second time this has happened,the first time I simply reinstalled Ubuntu thinking that I'd made a mistake somewhere. But this has happened again, on an install that was barely four hours old.

Here's the error:

```
Mount: Mounting /dev/hda2 on /root failed: invalid argument
Mount: Mounting /dev/hda2 on /dev/.static/dev failed: No such file or directory
Mount: Mounting /dev on /root/dev failed: No such file or directory
Target filesystem dosen't have /sbin/init

(some stuff about it using the built-in shell)

/bin/sh: can't access tty: job control turned off
```

Is this the work of some virus or exploit? It's like my fstab is getting deleted...along with messing up X.

---

