---
title: "Multidesktop Tips and Fixes"
date: 2009-11-01
forum: Desktop Environments
---

### Post by Netich on 2009-11-01
Hi, I thought it would be a good idea to have a thread to post tips and fixes about having multiple desktop installed.

I usually install kubuntu-desktop over ubuntu, but there are some annoyances as some of you will know. So you can post your tips, bugs you may find, or fixes to these bugs. Ill try to gather them and update the first post.

Ill start with two must-have applications. They group KDE applications in gnome menu, and gnome apps in KDE menu.

[Gnome Menu Extended]("http://www.gtk-apps.org/content/search.php?search=1&name=gnome%20menu%20extended")
[K Menu Gnome]("http://www.kde-apps.org/content/search.php?search=1&name=k%20menu%20gnome&user=ariszlo")


**How to switch between kdm and gdm:**
```
sudo dpkg-reconfigure gdm
```


**How to change the usplash after after adding a desktop:**

It seems that the last desktop we install override the default desktop. As you can read in this [post]("http://ubuntuforums.org/showthread.php?t=428061"), you can try selecting another one doing:
> $sudo update-alternatives --config usplash-artwork.so 

but if it doesnt work (like me) you can just uninstall **kubuntu-artwork-usplash** package through synaptic


And a bug:
When installing kubuntu-desktop in ubuntu, the mouse pointer of kde override the gnome one. If anyone know the fix, please post it.

---

