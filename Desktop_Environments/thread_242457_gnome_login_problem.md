---
title: "gnome login problem"
date: 2006-08-23
forum: Desktop Environments
---

### Post by ecbush on 2006-08-23
hello,

I'm having trouble loging in to a normal gnome session. When I try, it fails and refers me to the .xsession-errors file. the message there is:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "bush"
write wtmp entry: Input/output error

Gnome failsafe session works.

Any suggestions as to how to fix this?

thanks,
Eliot

---

### Post by mlind on 2006-08-24
Can you check if you're the owner of ~/.Xauthority and ~/.ICEauthority files  (and all other files .except lvm or rnd related) ? 

What is the output of:
```

ls -l ~/.Xauthority
ls -l ~/.ICEauthority

```

And output of:
```

ls -la | grep root

```

---

### Post by ecbush on 2006-08-24
I own both those files:

-rw------- 1 bush bush 312 2006-08-24 11:32 /home/bush/.Xauthority

-rw------- 1 bush bush 844 2006-08-23 17:13 /home/bush/.ICEauthority

and if I run  

ls -la | grep root

in my home directory the output is

drwxr-xr-x 10 root root   4096 2006-07-28 15:58 ..

thanks,
Eliot

---

### Post by tomski on 2006-08-24
i have a similar GDM problem but it has occured since the broken xserver package.
the only access to a desktop i have at the moment is via:

startx

at command prompt

any ideas?

---

