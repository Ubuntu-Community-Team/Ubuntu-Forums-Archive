---
title: "Help installing UT2004"
date: 2005-07-28
forum: Gaming &amp; Leisure
---

### Post by arcanistherogue on 2005-07-28
well, I cd'd over to the cdrom directory (/cdrom) and ran the linux-installer  script.  Then I got to the part where I needed to switch discs, and I couldn't unmount disc 1 to put in disc 2.  If i hit the button on the front of the drive it doesnt eject, and neither if I right click the cdrom icon and hit "eject" or "unmount".

How do I install this?

---

### Post by professor_chaos on 2005-07-28
And if you try
```
sudo umount /media/cdrom
``` 
in terminal???

---

### Post by arcanistherogue on 2005-07-28
[QUOTE=professor_chaos]And if you try
```
sudo umount /media/cdrom
``` 
in terminal???[/QUOTE]
john@ubuntu:~$ sudo umount /media/cdrom
umount: /media/cdrom0: device is busy
umount: /media/cdrom0: device is busy
john@ubuntu:~$

is the output.

---

### Post by arcanistherogue on 2005-07-28
I read somewhere else that you  have to copy the install script off the CD first, which I just did.  I started the install, and insterted disc 2, but it wouldnt read it.  I redid the install, starting with disc two this time, and it still asked for me to insert disc 2.  

I do not know what to do ;-;

---

### Post by strikeforce on 2005-07-29
This link might help you.

[http://www.linux-gamers.net/modules/wfsection/article.php?articleid=18](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=18)

I'm assuming your trying to install a linux ut2004 version.

---

### Post by Mishura on 2005-07-29
> I read somewhere else that you have to copy the install script off the CD first, which I just did. I started the install, and insterted disc 2, but it wouldnt read it. I redid the install, starting with disc two this time, and it still asked for me to insert disc 2.


I've never had any problems installing UT2004 on various distros (Tested myself:  Mepis, Kubuntu, Mandrake, Fedora).

How I do it:

1.  Copy the "linux-installer.sh" (or however its named) to your hard drive.
2.  Run it.  (as root, if you feel like) [#> sh ./linux-installer.sh]
3.  Mount discs as they are requested using either a terminal with "mount/umount" or whatever GUI method (storage:// in KDE works nicely.)
4.  Should be it.  Remember to upgrade to the latest patch, and install various extras and mods as you see fit ([http://liflg.org](http://liflg.org) is a great resource for easy-installable mods and patches).

Notes  (observations and stuff):

1.  The game installs in a rather odd order, Disc 2, 3, 4, 5?, and then back to 1.  It never asks for the "Play Disc".  Upon further inspection, the Play disc doesn't have any UT related files, just a bunch of Windows-only mod programs like UnrealED and stuff.   Practically useless in Linux due to the fact theres no CD checking  at runtime (Hell yeah!  Gotta love linux!).

---

