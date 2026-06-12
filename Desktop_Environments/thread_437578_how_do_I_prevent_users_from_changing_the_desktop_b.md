---
title: "how do I prevent users from changing the desktop background/wallpaper?"
date: 2007-05-08
forum: Desktop Environments
---

### Post by Abraxias on 2007-05-08
how do I prevent users from changing the desktop background/wallpaper with Ubuntu, Kubuntu, Edubuntu & Xubuntu:?:

I work for a high school that is considering switching to Ubuntu, Kubuntu, Edubuntu & Xubuntu (depending on the hardware).  one of the concerns the school has is preventing the students from changing the desktop background and using obscene wallpaper.  the school would rather keep the desktop backround a plain color and uniform with all of the computers used by the students.

I know how to do disable/lock the desktop with both Windows 2K & XP.
with Windows 2K/XP, I can:[LIST]
[*]Disable Active Desktop & Wallpaper
[*]Prohibit Changes
[*]Remove Display in Control Panel
[*]Prevent changing wallpaper[/LIST]

is it possible to prevent users from changing the desktop background/wallpaper with Ubuntu, Kubuntu, Edubuntu & Xubuntu:?:  if so, how:?:

if not, :idea: it would be a nice feature to be considered for the next release.  perhaps, :idea: allowing administrators the option to change the priveledges of the user and require administrator permission to change the desktop background/wallpaper.

---

### Post by Zelut on 2007-05-08
Well I have never done that before but after a little digging I think I'm close.  Take a look at the options inside gconf-editor in the directory here:

/apps/panel/default_setup/toplevels/bottom_panel/background/

it looks like you can specify a file or just color in that area.  Again, I haven't tested it but this may also set it locked.  Good luck there... if you need we can keep looking, but I think we're close.

---

### Post by FuturePilot on 2007-05-08
There a program in the repos called Pessulus.```
sudo apt-get install pessulus
```
> pessulus enables the system administrator to set mandatory settings in GConf, which apply to all users, restricting what they can do, which may be of particular usefulness for kiosks (internet cafes, for example).
Examples of what can be locked down are the panels (no changes in the panel configuration are allowed, locking their position and their contents), some of their functions individually (disabling screen locking and log out), the web browser (disabling specific protocols, arbitrary URLs, forcing the user to be in fullscreen mode), among many others.

---

### Post by Abraxias on 2007-10-08
I've been busy but have been meaning to reply back to this thread.

ru0n has recently sent me a private message, reminding me about this thread:
[QUOTE=ru0n]**Disabling background**
Hey, did you have any luck with disabling the background in your highschool?
If yes how?[/QUOTE]

unfortunately, none of the suggestions provided prior to this reply has helped me.  since I don't know how to prevent students from changing the desktop environment (background, icons, names of icons, etc.), I cannot recommend Ubuntu for the high school I'm working for.

---

### Post by ru0n on 2007-10-09
> **Abraxias said:**
> I've been busy but have been meaning to reply back to this thread.

ru0n has recently sent me a private message, reminding me about this thread:


unfortunately, none of the suggestions provided prior to this reply has helped me.  since I don't know how to prevent students from changing the desktop environment (background, icons, names of icons, etc.), I cannot recommend Ubuntu for the high school I'm working for.

Well i've managed to lock the icons and the names of icons by giving the rights of the icons to the administrator. Meaning that the current user can use (as example) firefox, but cant rename, delete or change anything with it.

The only thing i cant "lock/block" is the background... there must be a possibility.

---

### Post by snyw14 on 2007-12-28
Try to change the ownership of /.gconf/desktop/gnome/background/%gconf.xml at home directory to administrator and change the access mode to 644.
User can change the background but it only works for the current session, next session the background will be back to default.

---

### Post by snyw14 on 2008-01-04
change mode of  /usr/bin/gnome-appearance-properties fromi 755 to 744, so only root can akses this file to change the appearance of desktop

---

