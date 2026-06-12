---
title: "[SOLVED] Panel Shortcuts - Location?"
date: 2008-12-18
forum: General Help
---

### Post by chiefchief on 2008-12-18
Forgive me if there's a similar question in the forums.  I tried searching, but I don't think I have the proper syntax.

I'm administrating a couple linux boxes, and I'm trying to sneak shortcuts into their bottom panel (I have them down to only one), but I can't find the location in the /home/<user> folder.

Any help?

---

### Post by gettinoriginal on 2008-12-18
Are you talking application launchers ?? :confused:

---

### Post by chiefchief on 2008-12-18
Yes.  Like I said, syntax.  I want to put application launchers in their panels.

---

### Post by drs305 on 2008-12-18
Unfortunately none of this will export a panel from one computer to another, but if you wade through it you can get the commands and icon locations. But here are some locations where the data is stored:

The user's $HOME/.local/share/applications displays a list of user applications. If you right click, Properties, you can see the command.

$HOME/.gnome2/panel2.d/default/launchers shows default launchers placed on the panel.

For all apps, /usr/share/menu/<appname> contains a list of the run commands and icon locations.

You can save a copy of your panel by running. The data isn't user friendly - it references data in gconf by :
```

gconftool-2 --dump /apps/panel >~/Desktop/panel

```
To restore a panel to the same machine:
```

gconftool-2 --load ~/Desktop/panel && killall gnome-panel
```

This will take you to the panel info in gconf, but it is buried in lots of individual applet and object settings:
```
gconf-editor /apps/panel
```

---

### Post by gettinoriginal on 2008-12-18
Or you can just right click the panel and add a custom launcher.  :p

---

### Post by chiefchief on 2008-12-21
Thanks so much drs305!  I want to ssh into the box in question and copy the application launcher from one user profile to the other, so command line is exactly what I want.  Thanks again!

---

