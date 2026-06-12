---
title: "Autologin with no *DM."
date: 2008-10-25
forum: Desktop Environments
---

### Post by The Warlock on 2008-10-25
Hey, I'm running Openbox and trying to cut down on my startup time by removing GDM to shave off a few seconds. I know GDM can be set up to automatically log in, but it takes time and memory to do so. I've played around with other *DM programs, including XDM and SLIM, but they don't do auto-login.

I'd really like to dispense with all that entirely and just have the desktop come up. I know how to do this in Debian (with inittab) but Ubuntu uses upstart rather than sysvinit, so I'm a little lost. Anyone know how?

---

### Post by The Warlock on 2008-10-25
Nevermind, I got it.

If anyone else needs to know:

0) remove gdm, kdm, xdm, slim, or whatever it is that you have.

1) create a script to act as a replacement for /bin/login
```
#!/bin/bash
/bin/login -f username
```

2) make that script executable and put it in /usr/local/bin or something

3) edit the last line in /etc/event.d/tty1 to use it as an alternate login:
```
exec /sbin/getty -n -l /usr/local/bin/autologin 38400 tty1
```

4) add the line "startx" to your .bash_profile file

---

### Post by pelago on 2008-10-25
See [http://www.mythtv.org/wiki/index.php/Frontend_Auto_Login#Note_on_Ubuntu_Gutsy_.287.10.29_through_Hardy_Heron_.288.04.29](http://www.mythtv.org/wiki/index.php/Frontend_Auto_Login#Note_on_Ubuntu_Gutsy_.287.10.29_through_Hardy_Heron_.288.04.29) which talks about MythTV but can be used ok for other purposes, just by changing the username to autologin as.

---

### Post by The Warlock on 2008-10-25
Ack, I've just discovered a problem. This method starts up my window manager without a login just fine, but it screws up PolicyKit (or ConsoleKit, not entirely clear on the details) by listing my session as "inactive", which disables suspend, shutdown, and a whole bunch of other stuff.

Anyone know how to fix PolicyKit for this?

---

### Post by kerry_s on 2008-10-25
probably that log in script, may be try:

sudo apt-get install rungetty

exec /sbin/getty -n -l /usr/local/bin/autologin 38400 tty1
to 
exec /sbin/rungetty tty1 --autologin username

---

