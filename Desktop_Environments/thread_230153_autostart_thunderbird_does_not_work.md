---
title: "autostart thunderbird does not work"
date: 2006-08-05
forum: Desktop Environments
---

### Post by eidex on 2006-08-05
hi,

i want firefox and thunderbird to startup with gnome, so i added "alltray firefox %u" and "alltray mozilla-thunderbird" to the sessionmanager, firefox works just fine but thunderbird is not loaded. is there a log where i can see what has gone wrong? 

(alltray is a utility to minimize programs to the tray)

greetings

---

### Post by claretsfan on 2006-11-16
I can confirm this is the case in Edgy, too.  Anyone managed to solve it?  Wouldn't even mind using Evolution, but it's the same with that.

At the moment I have a launcher for Alltry Mozilla-Thunderbird on my desktop, which I use to fire-up the application into the tray (where it stays).  It would be nice for this to happen on bootup.

Incidentally, it works ok in KDE/Kubuntu, by dropping the launcher into the startup folder.

---

### Post by claretsfan on 2006-11-17
Ok- fixed it.  Just in case anyone's interested:

Download and install alltray (see [http://www.ubuntuforums.org/showthread.php?t=278623&highlight=alltray]("http://www.ubuntuforums.org/showthread.php?t=278623&highlight=alltray"))

Type "alltray" in a terminal and dock thunderbird by clicking on TB's window (anywhere)

Right click desktop- create launcher
Under "command"type- *alltray mozilla-thunderbird* (call it whatever sounds sensible- mine's "Launch Thunderbird")

Right click on launcher and select "make link"

Drop this link into /home/username/.config/autostart (you may have to enable hidden files in your home folder to do this- under "view" on the menubar)

Thunderbird should now start minimised with Ubuntu and sit in the tray quite happily. 

Hope that's useful?

---

