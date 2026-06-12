---
title: "gnome (feisty) startup programs"
date: 2007-06-26
forum: Desktop Environments
---

### Post by dbbolton on 2007-06-26
for some reason, my custom startup programs aren't working. i've tried two methods.

1. System > Prefs > Session > Startup Programs
2. manually adding .desktop files to ~/.config/autostart/

example: ~/.config/autostart/conky.desktop
```
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=No name
Name[en_US]=Conky
Exec=conky
X-GNOME-Autostart-enabled=true
```

---

### Post by grigio on 2007-06-27
After the session starts is 'conky' present (try gnome-system-monitor)? it could be that conky starts too soon and then it isn't displayed

---

### Post by dbbolton on 2007-06-27
ok. i'll try making another program startup and see if it works :)

---

### Post by gasparov on 2007-07-08
I had a similar problem, not entirely similar...maybe it can help you

After emerg.....ops... installing beagle on my laptop I found out that something was wrong with the installation script in the deb, I haven't researched further but it seems that there is something wrong with permissions.
On gentoo:

```
gas@gentoo ~ $ ls -al .config/
total 10
drwx------   6 gas users  184 Sep 13  2006 .
drwxr-xr-x 119 gas users 5312 Jul  8 13:10 ..
-rw-------   1 gas users  832 Aug  5  2006 Trolltech.conf
drwx------   2 gas users  496 Jul  1 16:18 autostart
drwx------   2 gas users   80 Jul  7 20:36 gtk-2.0
drwxr-xr-x   2 gas users   80 Jun  1  2006 last.fm
drwxr-xr-x   3 gas users  160 Apr 20 18:26 menus

```

On ubuntu (no laptop now)  the autostart directory was
```

drwxr-xr-x   2  root root

```

as you can see you launch those gnome config programs ( Sessions---> Startup programs ) as users and hence you can't write the config there, solution is chown to your username ot make it world writeable with more security issues ( i think).

My laptop has a new ubuntu installation ( very nice ) and is the first time i go in that directory, I think that this is a bug....

---

