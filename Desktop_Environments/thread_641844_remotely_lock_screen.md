---
title: "remotely lock screen"
date: 2007-12-15
forum: Desktop Environments
---

### Post by rouble on 2007-12-15
Hi,

Say, I left my Ubuntu 7.10 desktop unlocked at work. I have ssh access to this box.

Is there a way to ssh into the box, and lock the screen? I have tried:

~$ env DISPLAY=:0 XAUTHORITY=/home/rouble/.Xauthority /usr/bin/gnome-screensaver-command --lock
** Message: Screensaver is not running!
~$

But that does not work. Is gnome-screensaver-command looking for some other environment variables?

tia,
rouble

---

### Post by -error on 2007-12-16
(assuming that you're using xscreensaver and your $DISPLAY set correcty) i suggest you first to check if xscreensaver daemon running on that screen.just do `ps ax | grep xscreensaver' and see if it prints pid of xscreensaver process. if it is - then `xscreensaver-command -lock' will do the job. if not - start it first by issuing `xscreensaver &'

---

### Post by rouble on 2007-12-16
Ubuntu 7.10 uses Gnome 2.20.1. In this version of gnome, gnome-screensaver-command is the application used to lock the screen and handle the screensaver, not xscreensaver.

From what I can tell, xscreensaver is not even installed, by default, on Ubuntu 7.10.

---

### Post by Michiel van Leening on 2008-02-20
Hi,

Don't know if it'll help you, but maybe it will help someone else.

Have a look at [http://ubuntuforums.org/showthread.php?t=632580](http://ubuntuforums.org/showthread.php?t=632580)

It helped me :-)

---

