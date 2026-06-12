---
title: "gnome broken"
date: 2006-09-08
forum: Desktop Environments
---

### Post by schias on 2006-09-08
after the last compiz (csm) update my gnome is not starting up correctly anymore. if i log in all i see is a white screen. a white cube to be correctly. it looks like the cube plugin is the only thing thats working. my compiz was starting with a line in the sessionsmanager of gnome. something like: compiz --replace &. i read in the forum that i have to change this line, but i dont know how i can do this, because i cant log in to gnome. i hope somebody can help me!

---

### Post by tuxinvader on 2006-09-08
After you log in, press CTRL + ALT + F1 to get to a console. Then you can login with your user/pass and edit the file. 

sudo nano /path/to/the/file/you/want/to/edit

then run

sudo /etc/init.d/gdm restart

Cheers

---

### Post by schias on 2006-09-08
thanks for the help, but my problem is that i dont know the path to the file i want to edit. do you know where gnome is storing the programs to start up if you log in?

---

### Post by tuxinvader on 2006-09-08
If I was a betting man I would go for /etc/gdm/gdm.conf-custom

---

### Post by tuxinvader on 2006-09-08
If I was a betting man I would go for /etc/gdm/gdm.conf-custom

---

### Post by ayoli on 2006-09-08
the graphical way: choose "gnome failsafe" in gdm login screen, then login change what you want, quit gnome and lagin again
btw if you have latest compiz, you need to:
```
sudo aptitude purge gnome-compiz-manager
```
which is no longer used and install:
```
sudo aptitude update && sudo aptitude install compiz-manager
```
then in menu System > Preferences > Sessions
pick startup programs tab and remove / disable all compiz entries if any and add an entry with ths command:
```
/usr/bin/compiz-manager
```

---

### Post by ayoli on 2006-09-08
> **tuxinvader said:**
> If I was a betting man I would go for /etc/gdm/gdm.conf-custom

compiz startup commands shouldn't be in gdm.conf-custom

---

### Post by schias on 2006-09-08
it didnt help anything. in the failsafe-mode i have no windowdecorator but everything else is working. the normal mode is still just showing a white screen. and all thats working there is the cube-plugin. does anyboda know which packages i have to have installed? i have: compiz, compiz-core, compiz-gnome, compiz-manager, compiz-plugins, compiztools, csm, cgwd and cgwd-themes.

---

### Post by tuxinvader on 2006-09-08
As may already be aparent I don't run compiz, but if you want to switch it off, you could remove the XGL server from gdm.conf-custom. That'll stop compiz being able to render and you should revert back to your boring old 2D desktop. Not as pretty, but atleast you'll have a GUI.

---

### Post by schias on 2006-09-08
i think that if i change the startupprograms for the gnome session in the failsafe-mode it doesnt have any affect on the normal session. because if i turn of the line with compiz, the cube is still working in the normal session (but still nothing else). i would really like to know where i can edit the programs gnome is starting up manually. does anybody have a idea?

---

### Post by Azathoth_ on 2006-09-08
Schia I had the same problem, after formatting the partition of Ubuntu and restoring my system from a previous backup.
After a lot of time (more than a day) i solutionated the problem, and for my was i needed to restore my kernel (the image and the linux-restricted-modules) and after, i reinstalled compiz and everything is ok.
Try this i think it'll help you

---

### Post by schias on 2006-09-08
at the end i found out what went wrong. i dont know why but i had a file called .gnomerc in my home directory. in this file was the old starting-up command. i deleted it and now everything is working fine again. thanks for the help. cheers

---

