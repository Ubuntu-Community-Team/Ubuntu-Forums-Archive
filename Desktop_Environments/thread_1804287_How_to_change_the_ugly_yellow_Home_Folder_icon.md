---
title: "How to change the ugly yellow Home Folder icon?"
date: 2011-07-14
forum: Desktop Environments
---

### Post by smug9001 on 2011-07-14
Every time I open a folder the Home Folder icon appears in Launcher. Is it possible to change this icon? I tried changing the user folder icon and I changed the desktop icon for the home folder, but the launcher doesn't reflect this.

Here's the screenshot to show you what I mean:

[http://ubuntuone.com/p/14Tz/](http://ubuntuone.com/p/14Tz/)

I want to change the launcher "Home Folder" icon that shows up when nautilus is started.

---

### Post by Frogs Hair on 2011-07-14
Open the file browser by running ```
gksu nautilus
``` in the terminal . Use the following path . file system/usr/share/icons .

Locate the icon set in use , you can check this in Appearance Preferences. Enter the places folder of the icon set in use and choose the folder which  holds the size of the icon being used in the launcher. 

Replace the plain folder image (no animation arrows) with one of your choice. The icon must be the correct size and use the same file name , svg , png , or other. This may not work with every icon set . Restart or log out/in may be required .

---

