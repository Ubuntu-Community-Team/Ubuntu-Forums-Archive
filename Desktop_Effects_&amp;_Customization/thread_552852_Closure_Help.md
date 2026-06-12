---
title: "Closure Help"
date: 2007-09-17
forum: Desktop Effects &amp; Customization
---

### Post by crazyhunk on 2007-09-17
Hello...

I recently found 'CLOSURE' .... and installed it, since i do not use the gnome power manager i found it to be a good alternative to shutdown/reboot... with some eyecandy tooo... and i very much liked it ... except for that i have one small problem.... none of the commands actually work.... I was wondering if anyone here got it to work .... 

Thanx... [:)]

---

### Post by praet on 2007-09-17
I believe that you need to set the individual commands for button actions.  Open closure preferences and set the commands you want to run.
```
gconf-editor
```
Browse to:
/apps/closure/commands

and set the following:
/apps/closure/commands/lock = xscreensaver-command -lock
/apps/closure/commands/logout	  = gnome-session-save --kill --silent
/apps/closure/commands/reboot	 =  sudo /sbin/reboot
/apps/closure/commands/shutdown = sudo /sbin/shutdown -h 0

---

### Post by crazyhunk on 2007-09-17
i just see now that the commands do work if i run closure from the terminal ... but does not work otherwise...
so i was wondering is htere something I need to do .. for it work without terminal

---

### Post by praet on 2007-09-17
How are you launching the app?
 are you running from sessions?
 are you launching manually (Alt+F2)?

---

### Post by crazyhunk on 2007-09-17
I have it in sessions...... and it is positioned on my gnome panel in place of the regular 'shutdown/retsrt/.....' button....

---

