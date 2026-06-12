---
title: "Can't login to Gnome (libgnutl.so.11 is missing)"
date: 2005-12-15
forum: General Help
---

### Post by Cyrus on 2005-12-15
Hi there I have a very bad problem:

When I try to login to Gnome I get:
```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "username"
/etc/gdm/Xsession: Beginning session setup...
/usr/bin/gnome-session: error while loading shared libraries: libgnutls.so.11: cannot shared object file: No such file or directory
```

How can I fix this?

---

### Post by bb002 on 2005-12-15
I looked in synaptic and that file is part of the "libgnutls11" package.

press alt+ctrl+f1 to drop to a tty. then type in "sudo apt-get install libgnutls11". 
If it tells you that you already have the newest version you will have to reinstall the package. Unfortunately I don't know howto reinstall packages without using synaptic.


But if apt-get does install the package restart your pc with "sudo reboot". Rebooting may not be necessary but let's play it safe.

---

### Post by Cyrus on 2005-12-15
Thanks for that:

I did sudo apt-get libgnutls11 --reinstall and now it seems to work ...

---

