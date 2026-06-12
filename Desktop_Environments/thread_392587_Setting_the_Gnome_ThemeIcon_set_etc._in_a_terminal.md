---
title: "Setting the Gnome Theme/Icon set etc. in a terminal"
date: 2007-03-24
forum: Desktop Environments
---

### Post by chell on 2007-03-24
Hello everyone! 

I just wanted to know whether it's possible to set GNOME's theme, icon set, metacity theme, wallpaper etc. via command line commands (i.e. not graphically) and if so, which commands  I need. 

Thanks in advance! 

chell

---

### Post by ardchoille42 on 2007-03-24
> **chell said:**
> Hello everyone! 

I just wanted to know whether it's possible to set GNOME's theme, icon set, metacity theme, wallpaper etc. via command line commands (i.e. not graphically) and if so, which commands  I need. 

Thanks in advance! 

chell

Change themes in gconf via the CLI
----------------------------------------------
To change the gnome splash image
```

gconftool-2 --type string --set /apps/gnome-session/options/splash_image "splash/name-of-splash-image-file"

```To change the wallpaper
```

gconftool-2 --type string --set /desktop/gnome/background/picture_filename "/path/to/wallpaper-file"

```To change the GTK2 theme
```

gconftool-2 --type string --set /desktop/gnome/interface/gtk_theme "name-of-gtk2-theme"

```To change the Metacity theme
```

gconftool-2 --type string --set /apps/metacity/general/theme "name-of-metacity-theme"

```To change the icon theme
```

gconftool-2 --type string --set /desktop/gnome/interface/icon_theme "name-of-icon-theme"

```

You need to also include the quotes just as typed above. You can do almost everything via gcontool-2. man gconftool-2 for more info.

---

### Post by chell on 2007-03-25
Thanks a lot mate! You've made my day!!!

---

