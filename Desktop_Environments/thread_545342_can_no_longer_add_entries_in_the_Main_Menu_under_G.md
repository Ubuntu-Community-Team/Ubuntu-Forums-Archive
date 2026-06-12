---
title: "can no longer add entries in the Main Menu under Games or Graphics"
date: 2007-09-07
forum: Desktop Environments
---

### Post by kevinfishburne on 2007-09-07
I'm using Feisty and GNOME on an AMD64 box. This sounds extremely crazy, but for some reason under the Games and Graphics categories in the main menu I can no longer create items/launchers. After clicking OK/Close they simply don't appear in the menu. I can modify existing ones in both categories and create new ones in every other category.

I believe I installed PlaneShift or some game as root and wonder if that somehow could have caused the problem, but don't know enough about how the main menu is generated/stored to know. On that note, where is the main menu stored so I can examine the permissions and such?

Something else odd that may be related... I copied that profile to the /etc/skel directory and created a new user. When I logged in as the new user the main menu was not the one from the copied profile, neither was it the default main menu. The Debian category was enabled and a few other things were jacked up. Very strange...

Kevin

---

### Post by swisscow on 2007-09-07
Possibly something has changed it's permissions and become root. Could be the permissions of home/.local

Used to happen to me when installing googleearth

---

### Post by kevinfishburne on 2007-09-10
I logged in with the root account and even it is unable to add desktop entries to those categories. Does anyone know how the main menu works? Does it just automatically pull .desktop files from known locations? If so where are those locations? I searched the filesystem for .desktop files and it found them all over the place.

---

### Post by kevinfishburne on 2007-09-10
Made some "progress". I went to edit the main menu, clicked the Revert button, and restored the menu to its defaults. Interestingly it changed but not to the default settings. It changed to the same settings I saw when I'd copied my home directory to /etc/skel and created a new user. The Debian menu was active, etc. I looked in the Debian menu and saw all the test entries I'd been trying to create in the Games and Graphics menus.

So... Why when creating a desktop entry in the Games or Graphics menus would they appear only in the Debian menu?

---

