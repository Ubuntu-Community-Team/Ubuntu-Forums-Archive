---
title: "Customize gnome desktop popup menu - how?"
date: 2006-08-03
forum: Desktop Environments
---

### Post by dda on 2006-08-03
Hi!

I want to add "Start Terminal" menu item to the gnome desktop menu (the one wich pops up when I right-click on desktop. How that can be done?

Thanks,
Dmitry.

---

### Post by canadianwriterman on 2006-08-03
Do this:

**Applications > Accessories > Terminal**

Right click on Terminal and select:

**Add this launcher to panel**

The Terminal launcher will be placed on the top panel, but you can drag it down to the bottom panel, if you prefer it there. Hope that helps.

---

### Post by ciscosurfer on 2006-08-03
Go to this folder```
cd ~/.gnome2/nautilus-scripts
```if it doesn't exist, create it.```
sudo mkdir ~/.gnome2/nautilus-scripts
```When you get there, create a new file.  Click the file to open it.  Enter the following into the file and then save it as start terminal or whatever you'd like to call it```
#!/bin/bash
# Open Gnome-terminal
cd $NAUTILUS_SCRIPT_CURRENT_URI
exec gnome-terminal
```The cool thing about my script here is that you can open a terminal in whichever you folder you are in and it will take you to that folder.

Make this script executable, etc.```
sudo chmod 755 ~/.gnome2/nautilus-scripts/NAME_OF_YOUR_FILE
```Exit out of your terminal, open up the previously mentioned folder and click reload to make sure the permissions took (or right-click the file you created and make sure the permissions were applied) Close out. 

EDIT: re-enter a terminal, and issue the following for the menu to take:```
kill -HUP *pid_of_nautilus* 
``` Right-click your desktop or within any folder and you should see a menu...have fun! :grin:

---

### Post by dda on 2006-08-03
Thanks **ciscosurfer**! I guess adding the menu item into "main" menu, not to the "Scripts" submenu, requires hacking sources. But I'm fine with "Scripts" submenu! =D> 

**canadianwriterman**, thanks for the tip, but that was not waht I needed. ;)

---

### Post by dda on 2006-08-03
Forgot to mention: I had to send "HUP" to nautilus process to make the "Scripts" submenu visible.

---

### Post by ciscosurfer on 2006-08-03
@dda
No problem!  Glad you like it!  Whoops :roll:...forgot to mention the need to kill -HUP nautilus' pid to make it show...but seems like you figured it out though :grin:

---

### Post by cmh on 2006-12-05
Using the scripts directory is a good start, but let's say I had a bunch of profiles for said terminal, and wanted to be able to group them under submenus... ie, a group for all the HP-UX systems I connect to, etc... 

Any way to add a custom menu to that list?

---

### Post by cmh on 2006-12-05
Ah jeez, coworker figured it out and made me look dumb. :)

Create subdirectories!

---

### Post by ciscosurfer on 2006-12-05
> **cmh said:**
> Ah jeez, coworker figured it out and made me look dumb. :)

Create subdirectories!*drumroll* ... tada!

---

### Post by gsyoungblood on 2007-04-24
From universe:

apt-get install nautilus-open-terminal

Other interesting and possibly useful ones:
nautilus-actions
nautilus-image-converter
nautilus-script-audio-convert
nautilus-script-collection-svn
nautilus-script-manager
nautilus-share

Note: Confirmed in feisty.

---

### Post by jbdavid on 2007-08-09
> **dda said:**
> Hi!

I want to add "Start Terminal" menu item to the gnome desktop menu (the one wich pops up when I right-click on desktop. How that can be done?

Thanks,
Dmitry.

This is such a BASIC thing.. EVERY (unix/linux system I have had let me open a terminal with a the right mouse button.   Since I do so much work on the terminal.. I downloaded the Fedora distro as probably being better for my use model..   
It would be REALLY nice if ubuntu had an "advanced menus for experienced *nix users" configuration option -- as I'm assuming someone somwhere must have decided that the command line was too confusing for the new linux users we want to attract ??? 
Maybe I'm whining in the wrong place.. but I hope to try out the solutions suggested here before I Install that Fedora download ... (wait that last one is months old already.. not too much time to play with this old box.. )
Jbd

---

### Post by jbdavid on 2007-08-09
> **gsyoungblood said:**
> From universe:

apt-get install nautilus-open-terminal

Other interesting and possibly useful ones:
nautilus-actions
nautilus-image-converter
nautilus-script-audio-convert
nautilus-script-collection-svn
nautilus-script-manager
nautilus-share

Note: Confirmed in feisty.
---
THAT was TOO easy!! Thanks!  - now there is hope for Ubuntu!

---

### Post by ggaaron on 2007-11-02
Had someone figured the way to edit the "main" right click desktop menu?

Is there a way to add icons to this scripts.

Thanks in advance!
Aaron

---

