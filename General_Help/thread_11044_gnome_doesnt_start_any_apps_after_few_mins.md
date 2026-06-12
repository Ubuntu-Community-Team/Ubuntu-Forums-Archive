---
title: "gnome doesnt start any apps after few mins"
date: 2005-01-13
forum: General Help
---

### Post by disisit on 2005-01-13
hi,

strange thing.. when i boot the live cd (most recent version) all works fine, but after a few minutes and after i have started some apps, i cant start any new ones, the mouse cursor displays a hourglass for a few secs, but nothing happens.
i rebooted and watched a root shell:

```
root@ubuntu:/var/log # tail -f XFree86.0.log
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
AUDIT: Sat Jan  8 01:19:30 2005: 3321 X: client 24 rejected from local host
AUDIT: Sat Jan  8 01:19:40 2005: 3321 X: client 21 rejected from local host
AUDIT: Sat Jan  8 01:19:40 2005: 3321 X: client 21 rejected from local host
AUDIT: Sat Jan  8 01:19:56 2005: 3321 X: client 21 rejected from local host
AUDIT: Sat Jan  8 01:20:00 2005: 3321 X: client 21 rejected from local host
AUDIT: Sat Jan  8 01:20:01 2005: 3321 X: client 21 rejected from local host
AUDIT: Sat Jan  8 01:20:05 2005: 3321 X: client 21 rejected from local host
AUDIT: Sat Jan  8 01:20:12 2005: 3321 X: client 21 rejected from local host
AUDIT: Sat Jan  8 01:20:15 2005: 3321 X: client 21 rejected from local host
AUDIT: Sat Jan  8 01:20:40 2005: 3321 X: client 19 rejected from local host
AUDIT: Sat Jan  8 01:20:40 2005: 3321 X: client 19 rejected from local host
AUDIT: Sat Jan  8 01:20:44 2005: 3321 X: client 19 rejected from local host
AUDIT: Sat Jan  8 01:20:44 2005: 3321 X: client 19 rejected from local host
AUDIT: Sat Jan  8 01:20:49 2005: 3321 X: client 19 rejected from local host
AUDIT: Sat Jan  8 01:20:59 2005: 3321 X: client 19 rejected from local host
AUDIT: Sat Jan  8 01:21:07 2005: 3321 X: client 19 rejected from local host
```
and 
```

root@ubuntu:/var/log # xman
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Error: Can't open display: :0.0
```

my machine is a athlon 800mhz, 512 ram, 128mb graphics (kyro chip)

any clues?  :confused: 

greetings!

---

### Post by ricpelo on 2005-01-13
Did you configure the network?

It seems the known problem about to change the hostname.

See [https://bugzilla.ubuntu.com/show_bug.cgi?id=2631](https://bugzilla.ubuntu.com/show_bug.cgi?id=2631) for details.

The workaround could be to change the hostname to 'macaroni':

hostname macaroni

Good luck.

---

### Post by disisit on 2005-01-14
thanks, that fixed it!

---

