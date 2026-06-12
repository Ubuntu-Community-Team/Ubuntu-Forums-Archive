---
title: "XGL session problems"
date: 2006-06-19
forum: Desktop Environments
---

### Post by myha on 2006-06-19
Hi all,

I am having problems with logging onto my xgl session....
When I try to login I get the following error (.xsession-errors):
```

Your session only lasted less than 10 seconds. If you have not loged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem.
```

~/.xsession-errors:
```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:20.Xservers" -h "" -l ":20" "mihap"
/etc/gdm/Xsession: Beginning session setup...
No profile for user 'mihap' found
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  1 (X_GLXRender)
  Serial number of failed request:  98
  Current serial number in output stream:  99

(gnome-session:3082): Gtk-WARNING **: cannot open display:

```

Any idea? Btw I have more than enough disk space...

regards,

---

### Post by woedend on 2006-06-19
can you list your hardware, your drivers, and your gdm.conf-custom ?
Also, do you use the xgl repo's (beerorkid) or ubuntu's?

---

