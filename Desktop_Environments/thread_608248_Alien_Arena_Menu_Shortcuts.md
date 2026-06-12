---
title: "Alien Arena Menu Shortcuts"
date: 2007-11-09
forum: Desktop Environments
---

### Post by gdi2k on 2007-11-09
Hi, 

Alien Areana is a very cool game. However, installing it is a matter of unzipping an archive to a directory. Of course, this results in no Gnome menu links to the game. 

How can I add a menu item for all users (or any users added in the future)?

---

### Post by gdi2k on 2007-11-09
Ok, got it figured out with help from a friend, here's the solution for those looking in the future:

In /usr/share/applications add a .desktop file for it. The files are simple, check a few examples. 

I also had to create a script to change to the Alien Arena directory before launching the game, otherwise it wouldn't start. Mine looks like this: 

```
#!/bin/bash

cd /usr/share/games/alienarena2007
./crx

```

---

