---
title: "Login Screen App Removed in 9.10 ???"
date: 2009-12-28
forum: Desktop Environments
---

### Post by misteralexander on 2009-12-28
On [ [https://help.ubuntu.com/community/UbuntuEyeCandy](https://help.ubuntu.com/community/UbuntuEyeCandy) ] it states:

> 
The login window is also sometimes called the Gnome Display Manager, or GDM.

*Click System &#8594; Administration &#8594; Login Window. 

To install new login screen themes, save the .tar.gz with your theme on it to the directory of your choice. In the Login Screen program, press the Install New Theme button, find your new theme's file, and press the Install button.

Then simply select the new theme from the list of available themes. You can also set it up to pick a random theme on every boot, rather than picking just one theme.


Well, I navigate to where it says, but the program that launches is TOTALLY different than in 9.04.  Instead of giving me all sorts of options, it just a small box that only lets me alter automatic / manual login.  WTF??? In all fairness, my 9.04 install was a single user system, my 9.10 install has 3 users. I don't know if or why that would make a difference.

PLEASE HELP!

---

### Post by craftomaniac on 2009-12-29
Hello.

It appears they changed GDM and removed gdmsetup in Karmic. That removed the ability to use those GDM login screen themes.

Fortunately, you can still change some settings.
```
gksudo -u gdm gnome-appearance-settings
```
With that, you can change the background, GTK theme, and fonts for the gdm login screen. It's like configuring Ubuntu's theme except for the login screen.

Here are more links on that:
[http://ubuntuforums.org/showthread.php?t=1292533](http://ubuntuforums.org/showthread.php?t=1292533)
[http://wiki.archlinux.org/index.php/Gnome_2.28_Changes#Configuring_gdm_2.28](http://wiki.archlinux.org/index.php/Gnome_2.28_Changes#Configuring_gdm_2.28)

---

