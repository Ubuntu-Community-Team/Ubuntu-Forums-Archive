---
title: "gnome-panel crashes and loop crashing"
date: 2005-10-03
forum: Desktop Environments
---

### Post by huzzzo on 2005-10-03
hi there, 
I don't know if this is the correct section or it's prefer to post this topic in the bug section.

anyway I have a problem on my user in ubuntu (only in one user):
when i start session with my user and pwd, gnome-panel crashes and it tries to restart, but it crashes again. 
I have tried to backup and rename .gnome and .gnome2 directories, but it still crashing.

Anyone could help me? I would save my setting (thunderbird and firefox in particoular).

---

### Post by fabiand on 2005-10-06
Hey,

thats a problem in gconf ...
so: logoff in gnome and press <Ctrl><Alt>+<F1> .. 
enter your username and password
I DON'T GUARANTEE ANYTHING
delete the folder .gconf*
all configurations made to the gnome desktop will be lost!!

- fabiand

---

### Post by bestgun on 2006-06-01
I was having the same problem...see this thread:

[http://ubuntuforums.org/showthread.php?t=14853](http://ubuntuforums.org/showthread.php?t=14853)

The hint is to delete ".recently-used" from home directory.
I solved my problem in  Breezy Badger 5.10 Release.

I Hope this resolves your problem.

---

