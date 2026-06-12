---
title: "KDE won't GUI Login"
date: 2006-01-03
forum: General Help
---

### Post by theaffman on 2006-01-03
when the computer starts up, the login screen comes up, i enter my pass word, the screen then flashes and the login screen comes up again.  I can login but only without the GUI, and as i have yet to learn alot about linux i don't know what to do from there.

Please help, I like ubuntu.  But I don't reall like the idea of a fresh install.

---

### Post by Pawel Stolowski on 2006-01-03
Looks like your session is ended up immediately... Set your session type (use Session menu on the login screen) to GNOME or KDE and see if it helps.

---

### Post by gnu2tux on 2006-01-03
Hi, 

 When you are at the log in screen, press ctrl+alt+f2

log in to the text prompt, then type the following:

```

$sudo /etc/init.d/gdm stop (if you use the gdm login system)
or
$sudo /etc/init.d/kdm stop (if you use the kdm login system)

then, start up the x server manually:

$startx

```

if still no joy, then what is the error message you get in the log file:

/var/log/Xorg.0.log

the main errors are preceded with (EE) and (WW) infront of them, making them easier to identify.

The following will reconfigure the x server:
```

sudo cp /etc/X11/xorg.conf xorg.conf.backup
$sudo dpkg-reconfigure xserver-xorg

```

Regards,

Al.

---

