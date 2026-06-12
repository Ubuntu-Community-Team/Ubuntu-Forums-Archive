---
title: "Where are all my applications?"
date: 2009-05-17
forum: General Help
---

### Post by Vostrocity on 2009-05-17
Where are they? I'm trying to add launchers to AWN. I've found some (like Firefox and GIMP) in /usr/bin but not others (like Google Earth and Terminal).

---

### Post by x33a on 2009-05-17
look in /bin, /sbin/, /usr/bin, /usr/sbin,/usr/local/bin, /usr/local/sbin.

---

### Post by jbruced on 2009-05-17
You can also do a find in terminal, like if you're looking for firefox do:

sudo find / -name *firefox*

---

### Post by Legace on 2009-05-17
1) Open Text Editor (gedit)
2) Select the app that you want and drag it's icon from the GNOME menu into the text editor..

You should get something like:
```
[Desktop Entry]
Encoding=UTF-8
Name=Calculator
Comment=Perform arithmetic, scientific or financial calculations
Exec=gcalctool
Icon=accessories-calculator
NotShowIn=KDE;
Terminal=false
Type=Application
StartupNotify=true
Categories=GNOME;GTK;Utility;Calculator
X-GNOME-DocPath=gcalctool/gcalctool.xml
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gcalctool
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-OtherBinaries=gnome-calculator
X-Ubuntu-Gettext-Domain=gcalctool
```

The Exec entry (gcalctool in this case) is what you're searching for :)

---

### Post by Vostrocity on 2009-05-17
Thanks for the replies.

---

### Post by CatKiller on 2009-05-17
You can also use **which** to see where the executable is for a given command. For example, ```
$ which gnome-terminal
/usr/bin/gnome-terminal
```

When you're creating a launcher in AWN (or for the menu or Desktop, for that matter) you don't need to give the full path as long as the command is in your $path. You can just type the name of the command and it should just work, in some cases automatically picking the right icon for you.

---

### Post by Vostrocity on 2009-05-17
Thanks for the tips. I tried those but I found that it was easier to just copy the icons and commands from the shortcuts in my Applications menu.

---

### Post by soro2005 on 2009-05-17
Or you just drag them from the menu onto Awn. Or if that doesn't work, from the menu onto the desktop, and from there onto awn. :guitar:

---

