---
title: "Change netapplet tray icon?"
date: 2007-03-24
forum: Desktop Environments
---

### Post by eitan_a on 2007-03-24
I'm theming gnome right now and changing the system tray icons is a huge hassle, since they are located in different places.  I want to change the netapplet tray icon and cannot find where it's located.  Any help??

---

### Post by eitan_a on 2007-03-24
bump, any help?

I've found icons in /usr/share/icons/hicolor/24x24/apps/wireless*png but when I changed them it didn't change net applet's tray icon.

---

### Post by eitan_a on 2007-03-25
toot

---

### Post by mgmiller on 2007-03-25
You don't say which icon set you are currently using.  Look in system>preferences>themes and click the icon tab for the name of the icon theme you are using.  Then look in /usr/share/icons for that icon theme and then look in the various subfolders for the one you want.   For example, /usr/share/icons/Human/24x24/apps/gnome-netstatus.  there are a bunch of them.  You will also have to look in the 48x48/apps folder and also the scalable/apps folders.  If you are not using the Human icon set, just substitute the name of the one you are using.  If you are using an icon set that you installed from somewhere else, open your home folder and hit ctrl-h to make the hidden files visible and go to .icons.  In there you will find the icon sets you have installed.  Then follow the above instructions to find the icons you want to change.  I am using Dropline Neu! icons and I wanted to change it's Firefox icon.  This is how I did it.

---

### Post by eitan_a on 2007-03-25
Changing the icon theme doesn't change the netapplet icon, which leads me to believe it is located not in /usr/share/icons/ or ~/.icons but somewhere netapplet installs it.  The same thing happens with gaim...changing the icon theme doens't change your gaim icon.  I know people have edited this before, and I cannot find netapplet's icons anywhere yet.

---

### Post by mgmiller on 2007-03-25
Not all icon themes change all the icons everywhere.  Try installing Dropline Neu! icons from gnomelook.org and see if it changes it.  These can be found in the .icons folder after you install them in the theme manager.

---

### Post by eitan_a on 2007-03-25
Just tried Neu icons...they didn't change the netapplet icon nor my battery icon (which does change when changing themes) but a host of other desktop icons.  

I wonder, where is the netapplet source located?  I was also looking for it.  I wonder if I can find the location of the icons by searching through the code..

---

