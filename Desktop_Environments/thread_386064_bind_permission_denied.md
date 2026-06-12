---
title: "bind: permission denied"
date: 2007-03-16
forum: Desktop Environments
---

### Post by LordBender on 2007-03-16
I installed two days ago ubuntu edgy from the latest ISO image taken the same day.
Everything worked perfectly, I installed beryl and it worked too.

Then yesterday I enabled from sources.list the universe and multiuniverse repository and made an update and dist-upgrade.

Since then I'm not able to start GNOME, the only way to start it is to launch the failsafe GNOME version from gdm.

The error message in xsession-errors says only:

```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "valdos"
/etc/gdm/Xsession: Beginning session setup...
bind: Permission denied

```

but I can't figure out why. I installed kde too but I get the same error.  I suppose there is some problem with the xorg configuration or with gdm but I can't get what.

Someone has some idea? I'm pretty bored about the failsafe version :)
Thanks

---

### Post by ZERO_SHIFT on 2007-03-17
Try uninstalling beryl and installing the 0.2 version

---

### Post by LordBender on 2007-03-17
I tried to uninstall beryl and install the 0.2 version but I get the same error.
I even tried to uninstall beryl and reboot but it doesn't seem to change anything. I don't think it's beryl fault.

Thank you anyway for your suggestion :)

---

### Post by thexaspect on 2007-07-29
Ok, I'm having the same problem right now, and I don't even have beryl installed. has anyone been able to fix this? Ubuntu loads to GDM, put in username and pw, and up pops a menu that says:


"Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of these failsafe sessions to see if you can fix this problem. "

and then all of the same /etc/gdm/PreSession/Default and whatnot from the previous post. I didn't log myself out, and I'm certainly not out of diskspace. I can login to the recovery mode, as root, from grub, but I don't know where to start from there. Any ideas? Anyone? Please! I just got everything working again after my hard drive crashed. Thanks all =)

---

