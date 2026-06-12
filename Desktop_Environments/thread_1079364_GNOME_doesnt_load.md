---
title: "GNOME doesnt load"
date: 2009-02-24
forum: Desktop Environments
---

### Post by bhoot_jb on 2009-02-24
i installed ubuntu 8.10 on my desktop, ofcourse with GNOME desktop. everything was working fine.
Later on, i also installed KDE (full package) so that i could work with both the environments. I particularly liked KDE environment so i made it the default desktop env during startup.
Now my ubuntu has changed to kubuntu (the title at startup shows kubuntu).
But i have no issues with it. My real problem is now i cannot load GNOME environment. At login screen, after choosing GNOME session, i cannot go past the login screen. after entering login id and password, the screen goes blank...and the login screen comes back again.
I dont face this problem in loading KDE. Sometimes even it shows this behaviour - but only when i have attempted one or more unsuccessful login in GNOME. I hope u understood what i mean to say.
Is there any solution to this?
yaa..i can access all of my GNOME applications in KDE.
But i also want my GNOME env back so that i can use both KDE and GNOME as and when required.
Pls help me..

---

### Post by ddrichardson on 2009-02-25
You need to stop the display manager first but I don't know which one (there are three likely ones), open a second terminal by pressing Ctrl+Alt+F2. Then login to the terminal and type:
```
sudo /etc/init.d/gdm stop
```
If this fails try:
```
sudo /etc/init.d/kdm stop
```
Now backup your .xinitrc file:
```
cp ~/.xinitrc ~/.xinitrc.old
```
Create a new one that runs Gnome only:
```
echo "gnomesession" >> ~/.xinitrc
```
Run X by typing:
```
startx
```
When it fails you'll see what went wrong, post back and we'll see whats what.

---

