---
title: "Turned off dbus by accident!!!!!"
date: 2009-04-03
forum: General Help
---

### Post by JoaoMachado on 2009-04-03
I accidently unchecked the DBUS service, now my keyboard and mouse do not work on my laptop?

I went into the command line, and there it works, I started dbus by putting the command: sudo /etc/init.d/dbus start, and it started, but as soon as I log in, no keyboard or trackpad?

Help, it was working so nice before I screwed it up!
Ubuntu 9.04 on HP G60 laptop.

Joao

---

### Post by BGFG on 2009-04-03
When you say login, after 
```

sudo /etc/init.d dbus start

```
do you immediately run
```

sudo /etc/init.d GDM start

```
and lose the keyboard ?

---

### Post by JoaoMachado on 2009-04-03
> **BGFG said:**
> When you say login, after 
```

sudo /etc/init.d dbus start

```
do you immediately run
```

sudo /etc/init.d GDM start

```
and lose the keyboard ?


well, I just typed ```
gdm
``` at the command line and it took me to the login screen. I also tried just going into graphical, by typing ```
startx
```, same thing, no keyboard or trackpad, tried usb mouse..nothing, cursor just stays there even though the desktop completely loaded..

Joao

---

### Post by JoaoMachado on 2009-04-03
Had to reinstall!

[URL="https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/112102"]
https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/112102[/URL]

---

