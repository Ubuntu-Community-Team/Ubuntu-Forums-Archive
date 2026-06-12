---
title: "install a .desktop file"
date: 2011-01-15
forum: Desktop Environments
---

### Post by magowiz82 on 2011-01-15
Hi,
I created a script to reboot mine system in windows and I would like to add globally (for all users) a menu item that starts it , so I created win-reboot.desktop that contains :
```
[Desktop Entry]
Encoding=UTF-8
Name=Win Reboot
Comment=Reboot into Windows
Exec=/usr/local/bin/win-reboot.sh
Icon=/usr/share/pixmaps/win.jpg
Terminal=false
Type=Application
Categories=Application;System;
StartupNotify=true

```and I saved it in /usr/share/applications/ , anyway I don't see it in the menu, why?
Do I miss something?

---

### Post by Brandon Williams on 2011-01-15
First, double-check the permissions on the file. They should be 644 (i.e. rw-r--r--). Next, verify that other applications in the Application and System categories are showing up in your menu. If there aren't any with just those two categories that show up, then try adding another category to the list to see if the item shows up.

---

### Post by gmargo on 2011-01-15
You don't see it in the menu because the menu is generated from a cached idea of what the application directories contain.  The actual cache file is **/usr/share/applications/desktop.en_US.utf8.cache**.  The locale-based filename may differ for you.

To make a long story short, you can regenerate that cache file with this non-obvious command:
```

$ sudo dpkg-reconfigure python-gmenu

```Run that whenever you install or modify the .desktop file.

To see what that command actually does, see the package's post-installation file: **/var/lib/dpkg/info/python-gmenu.postinst**.  It amounts to a wrapper around the **/usr/share/gnome-menus/update-gnome-menus-cache** program.

---

### Post by magowiz82 on 2011-01-15
Checking .desktop file permissions and running ```
sudo dpkg-reconfigure python-gmenu

```
fixed the issue for me. 
Thank you

---

