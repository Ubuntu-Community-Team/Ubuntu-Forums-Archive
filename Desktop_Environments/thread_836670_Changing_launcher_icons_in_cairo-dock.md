---
title: "Changing launcher icons in cairo-dock"
date: 2008-06-21
forum: Desktop Environments
---

### Post by einfinger on 2008-06-21
anyone know how to do this ?

---

### Post by Deadmode on 2008-11-03
Right click on the launcher.  Click modify launcher.  Either browse for the image name or type in the path.  I use locate to find the svg or png that I'm looking for.  I think most application png and svg icons are kept in the /usr/share/icons/
But to make it simpler for me I just locate.
Example:
```
:~$ locate transmission.svg
/usr/share/icons/hicolor/scalable/apps/transmission.svg

```

---

### Post by fabounet on 2008-11-03
avoid putting some complete path, cause if you just write "transmission" for exemple, it will take the icon of the icon theme you choosed (Human, Tango, etc)
Then if you change the theme in the config panel, all your icons will change accordingly. ;-)

---

### Post by Deadmode on 2008-11-03
hmmm ya I suppose it would be better to make a copy of the image and put it in the ~/.cairo-dock/current_theme/launchers folder.  I've been doing it the other way.  Haven't run into that problem yet.  :) probably will soon.

---

