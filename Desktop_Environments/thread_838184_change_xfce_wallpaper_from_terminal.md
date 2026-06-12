---
title: "change xfce wallpaper from terminal"
date: 2008-06-23
forum: Desktop Environments
---

### Post by SOME1 on 2008-06-23
hi, 
I want to use webilder in xfce (it's a program that automatically download and change desktop wallpapers). 
This program support in gnome and kde or any other desktop (by specify a terminal command to switch the wallpaper). 

My question is - does anyone know how can I change xubuntu or xfce wallpaper with the terminal? 

thanks.

---

### Post by mali2297 on 2008-06-24
First, go to Settings Manager -> Desktop and create a new backdrop list. Then, if you want to have /path/to/image.png as backdrop, you can use this command line to change the list:
```

echo -e '# xfce backdrop list\n/path/to/image.png' > $HOME/.config/xfce4/desktop/backdrops.list && xfdesktop --reload

```

---

