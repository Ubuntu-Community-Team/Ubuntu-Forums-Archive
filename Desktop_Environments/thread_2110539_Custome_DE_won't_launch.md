---
title: "Custome DE won't launch"
date: 2013-01-30
forum: Desktop Environments
---

### Post by horizons187 on 2013-01-30
I created a custom DE from a guide I found online and this is my first attempt but whenever I choose it from the session menu it loads and tells me it can't find the related .sh file I have checked and triple checked the location and name of the files I'll post the related codes here so you can have a look.

The .sh file:

[PHP]compiz --user-root-window & #use compiz window manager
hsetroot -full ~/firefox_wallpaper.png & #use hsetroot for wallpaper
gnome-do & #use gnome-do for application launcher
cairo-dock -o #use the cairo-dock[/PHP]The .desktop file:

[PHP][Desktop Entry]
Encoding=UTF-8
Name=matsDE
Comment=Opens Mat's Custom DE
Exec=/home/mat/matsDE.sh
Icon=
Type=Application
X-Ubuntu-Gettext-Domain=gdm[/PHP]

---

### Post by zombifier25 on 2013-01-31
Try moving the .sh file into somewhere else, like /usr/bin.

---

### Post by m_duck on 2013-01-31
Also, check if /home/mat/matsDE.sh is executable. If it isn't, you can make it so either in by right-click -> properties in your file manager, or:```
chmod u+x /home/mat/matsDE.sh
```

---

### Post by Bucky Ball on 2013-01-31
A link to the guide you followed would be handy and helpful perhaps ...

---

