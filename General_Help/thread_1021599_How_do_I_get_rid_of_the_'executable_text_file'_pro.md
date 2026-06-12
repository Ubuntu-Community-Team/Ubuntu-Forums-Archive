---
title: "How do I get rid of the 'executable text file' prompt from a gedit made Launcher?"
date: 2008-12-25
forum: General Help
---

### Post by UbuObsidian on 2008-12-25
Help please. I'm so close to being done modding my Ubuntu.

---

### Post by didac on 2008-12-27
Righ-click on it, Properties, Permissions tab, uncheck 'allow executing file as a program'

---

### Post by UbuObsidian on 2008-12-27
Hey, thanks for the reply. :)

All changing the permissions seems to do is immediately launch the file in gedit instead of the Exec command I set inside the launcher text doc. Are there any special parameters that must be set in the launcher text file? Another thing that is very strange (I know this is a seperate issue) is that the .desktop extension doesn't become invisible once I set the file name on rename. Anybody know why that may be?

---

### Post by Coder543 on 2008-12-27
May I ask why you are creating a laucher in gedit??? Just go to the nearest gnome-panel.. right click.. add to panel.. custom application launcher.

---

### Post by UbuObsidian on 2008-12-27
> **Coder543 said:**
> **May I ask why you are creating a laucher in gedit???** Just go to the nearest gnome-panel.. right click.. add to panel.. custom application launcher.

I have several hundred files I want to do this to, for ease of use for someone else. Creating launchers one by one ain't gonna fly. I just need to get the formula for a launcher right so I can produce them in bunches.

---

### Post by mc4man on 2008-12-27
If you make desktop launchers (desktop configuration file) in a text editor then the name of the file at creation becomes the location name and can't be changed. 
You shouldn't have any trouble changing the display name either from inside the file or on a r. click rename.

There's no need to name it xxxx.desktop when creating, xxxx will do

It will only revert to it's creation name if the name='s inside are blank

Basic templates

```
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=
Type=Application
Terminal=false
Icon[en_US]=
Name[en_US]=
Exec=
Icon=
GenericName[en_US]=
```

```
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=
Type=Application
Terminal=true
Icon[en_US]=
Name[en_US]=
Exec=
Icon=
GenericName[en_US]=
```

```
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Link
Icon[en_US]=
Name[en_US]=
URL=
Name=
Icon=
```

---

