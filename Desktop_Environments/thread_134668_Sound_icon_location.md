---
title: "Sound icon location"
date: 2006-02-22
forum: Desktop Environments
---

### Post by Ramses de Norre on 2006-02-22
I think I've lost my volume icon.. On the systray I can still click on the volume app but I have to search a while for it, it has no icon.. and the icon disappeared also in an other application (saw it couple of days ago but I forgot which).
Anyone an idea where that icon should be? so that I can replace it with another one.

---

### Post by oakz on 2006-02-22
I think the volume control uses stock icons, located in /usr/share/icons/<your_theme>/<dimensions>/stock/media/stock_volume* (where <your_theme> is something like Human, gnome, gperfection2, etc and <dimensions> is something like 16x16, 24x24, or 32x32)

Take a look at your current theme and check if it supplies the stock icons for volume (there are a couple), a good reference to check for the icons that should be there is the stock "gnome" icon theme.

It not necessarily a bug if your current theme doesn't define these stock icons. Each theme can "inherit" the icons from another theme. For example, the Human theme only provides icons for some applications, mime types, etc, and relies on the gnome theme for everything else. Check which, if any, theme your current theme is based on by looking at /usr/share/icons/<your_theme>/index.theme. Look for the line containing "Inherits". If your current theme, or one it inherits, does not provide the stock icons, you can inherit from gnome to use the default volume icons.

---

### Post by Ramses de Norre on 2006-02-22
I just found another thread about the same ([http://ubuntuforums.org/showthread.php?t=113053]("http://ubuntuforums.org/showthread.php?t=113053")) and indeed it's just what you're saying, I added gnome to the inherits in the themes conf file and it's all fine now:) 
The inherits were set to a theme I don't have installed..

---

