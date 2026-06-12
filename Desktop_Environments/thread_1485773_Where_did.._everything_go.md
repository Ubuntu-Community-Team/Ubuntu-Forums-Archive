---
title: "Where did.. everything go?"
date: 2010-05-17
forum: Desktop Environments
---

### Post by tehMalone on 2010-05-17
Hi

I opened compiz-fusion-manager, and then something weird happened. My desktop icons, window decorations, keybindings and every keyboard input disappeared:/ What happened? I'm kind of a newbie

thanks in advance

my bottom panel disappeared as well

---

### Post by 3Miro on 2010-05-17
System crash, probably compiz and/or emerald and/or nautilus-desktop crashed. The easiest thing to do is to log out and log back in or to just reboot.

If you want to try a "harder" solutions, press Alt+F2 and type:
```
compiz --replace
```
this should return most of the functions back. I am not sure what the commands for the panel and desktop are, open terminal (Apps -> Accessories -> Terminal) and look for gnome-something-desktop/panel (type gnome- and hit tab twice to get all the options). You can also do "man gome-whatever-command-you-want-to-learn-about" and it will give you some help text.

---

### Post by tehMalone on 2010-05-17
Darn.. already did this.. I logged out, rebooted, did the compiz --replace thing, the gtk-window-manager --replace thing and all..

Killall gnome-panel makes my panels look right again, but since it removed my keyboard, (i can't press anything any more .. :/) can't do that anymore either.. I'm just happy that I have a xfce session as well right now ..

---

### Post by 3Miro on 2010-05-17
This is a big problem then. You can do the following test:

From the XFCE session, create a new user and then log in with that username and pass into Gnome session. If everything is working fine for the new user, then the problem is somewhere in the settings. Gnome settings are stores in .gnome-something and sometimes in .config in your home folder (/home/whatever-your-username-is). You can probably just delete those (well you probably want to keep a backup copy, so just rename them) and then try logging into Gnome again. You should note that .config also contains settings for other software, so you might want to get in it and delete/rename only some of the subfolders. Hopefully this will fix the issue.

(Other folders are .gconf, .gconfd and .nautilus, I am actually using xubuntu right now so I cannot give you a complete list)

If Gnome doesn't work for the new user either, then something is messed up with the default Gnome install. You will have to see how to reinstall all of Gnome (I actually don't know how to do this).

---

