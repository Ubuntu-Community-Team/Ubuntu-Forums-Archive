---
title: "Help With login and logout sound on Ubuntu 12.10"
date: 2013-12-03
forum: Desktop Environments
---

### Post by wolfzrat2 on 2013-12-03
Hi guys, I did some research on enable login and logout sounds on ubuntu. The only problem is that when I open the startup application window I dont see the gnome login and log out option in the list, I would add it but dont know how. So could someone please help. Thanks =)

---

### Post by fantab on 2013-12-03
Open 'Startup Applications' and "ADD":

Name = GNOMELogin Sound
Command = /usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOMELogin"
Comment = plays login sound

Then save it with 'Add'.

In 'System Settings' -> 'Sound' -> 'Sound Effects' -> 'Alert Volume' (adjust it accordingly)
Restart Ubuntu.

---

### Post by deadflowr on 2013-12-04
If you have your own sound file you can run with --file parameter
```
canberra-gtk-play --file /path/to/file
```
The fun thing about it is you can run a test in the terminal, to see if it works.

Sorry, though, don't know how to set about a log out sound.
There probably is a way, but never thought about it tell I saw this thread.

---

