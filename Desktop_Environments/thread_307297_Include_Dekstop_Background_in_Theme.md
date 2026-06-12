---
title: "Include Dekstop Background in Theme?"
date: 2006-11-26
forum: Desktop Environments
---

### Post by urukrama on 2006-11-26
Is it possible to include a desktop background in a theme, so that when I select a particular theme, my desktop changes automatically?

---

### Post by CowzRule on 2006-11-26
I'm assuming you're using Gnome. First select the desktop background that you want. Then go to System/Preferences/Theme. Adjust/Select the theme to your liking, then click the "Save Theme" button. Give your theme a name then click the check box titled "Save Background Image". That will assign your current desktop background to that theme.
Hope that helps :)

---

### Post by urukrama on 2006-11-26
Thanks for the reply. Yes, I am using Gnome, but apparently that feature is not there in Dapper.

EDIT: I assume I just have to add something to the theme file in ~/.themes, but I don't quite know what. I tried a few obvious possibilities, but none of them worked.

---

### Post by CowzRule on 2006-11-26
Here is the contents of one of mine```
[Desktop Entry]
Name=mytheme
Type=X-GNOME-Metatheme
Comment=
Encoding=UTF-8

[X-GNOME-Metatheme]
GtkTheme=Redmond
MetacityTheme=Galaxy
IconTheme=dlg-etiquette
BackgroundImage=/home/myname/.wallpaper/mywallpaper.png
```Notice the very last line.

---

### Post by urukrama on 2006-11-26
Many thanks! Exactly what I needed.:KS

---

