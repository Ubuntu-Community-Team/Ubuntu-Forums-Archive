---
title: "Gnome does not load"
date: 2005-04-29
forum: Desktop Environments
---

### Post by lizardking on 2005-04-29
I installed Kde from synatipc and then when I start it it says taht maybe the DCOP SERVE was not running so Kde shutdown. So I tray to run dcopserver in two ways:with my user and with sudo. I have also deleted the file  /home/lizardking/.DCOPserver_iac__0 w with rm beacuse dcopserver reports this:
```
---------------------------------
It looks like dcopserver is already running. If you are sure
that it is not already running, remove /home/lizardking/.DCOPserver_iac__0
and start dcopserver again.
---------------------------------
``` 
When I tryed dcopserver the terminal reports also this:
```
lizardking@iac:~ $ /usr/bin/X11/iceauth:  timeout in locking authority file /home/lizardking/.ICEauthority
``` 
So I turn back to gnome but now The splash and all gnome doesn not start like KDE and it is pretty funny that GDM and ICeWm and Enlightment works great!!!
**How can I do to come back GNOME?**   ](*,)

---

### Post by Xerampelinae on 2005-04-29
Does it give some sort of error when you try to start gnome?

What about trying this:

press ctrl+alt+f1, this should give you a console.. you probably have to log in..

```

sudo /etc/init.d/gdm stop
echo "exec gnome-session" > ~/.xinitrc
startx

```

See what that does.  If you want to get gdm back, either just reboot or do

```

/etc/init.d/gdm start

```

---

### Post by lizardking on 2005-04-29
I am with gnome now, after run **startx** .
So I must reports you the output of the code?

---

### Post by Xerampelinae on 2005-04-29
[QUOTE=lizardking]I am with gnome now, after run **startx** .
So I must reports you the output of the code?[/QUOTE]
 Huh.  If it worked there should be no problem.

On your login screen, I assume you're selecting a gnome session before you log in (it's in one of the menus or something)

---

### Post by lizardking on 2005-04-29
[QUOTE=Xerampelinae]Huh.  If it worked there should be no problem.

On your login screen, I assume you're selecting a gnome session before you log in (it's in one of the menus or something)[/QUOTE]
[SIZE=4]NO PROBLEM GNOME WORKS THANKSSS[/SIZE]
 :razz:  :razz:

---

