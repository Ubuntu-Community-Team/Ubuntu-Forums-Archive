---
title: "Customizing Screensavers"
date: 2009-08-16
forum: Desktop Environments
---

### Post by Tyson D on 2009-08-16
Hi, 

 I've set a goal for my self to be able to write some sort of screen saver from scratch by the end of august, but since Im an absolute begginer i figured i would start really small and just try and modify an exsiting one.

Ive been following this website
[http://www.freesoftwaremagazine.com/columns/customizing_your_screensaver](http://www.freesoftwaremagazine.com/columns/customizing_your_screensaver)

which basicly says make a copy, rename it, change the path to the picture you want to use, save.

im using a .jpg file just like he did but i cant figure out why it wont work. Any suggestions?

---

### Post by Tyson D on 2009-09-11
bump

---

### Post by Wardje on 2009-09-11
A quick try seemed to work flawlessly (though I must say I edited the contents with my ubuntu_theme.desktop as start point and didn't use his code as a base). So I'd say, try showing the exact contents of your .desktop file :) and perhaps go exactly by the ubuntu_theme.desktop contents to make your own screensaver


As a reference, my quick try:

```
[Desktop Entry]
Name=Floating GetFirefox
Comment=GetFirefox logo floating around the screen
Exec=floaters /home/ward/Pictures/firefox_support.png
TryExec=floaters
StartupNotify=false
Terminal=false
Type=Application
Categories=GNOME;Screensaver
```

---

### Post by Tyson D on 2009-09-13
ok so trying all this again.................ive managed to use a different picture from the /usr/share/pixmaps folder but i try and write a different directory in (/home/tyson/Pictures/filename) it doesnt seem to work.

this is what i have so far

[Desktop Entry]
Name=Floating Doughboy
Comment=Doughboy floating around the screen
Exec=floaters /home/tyson/Pictures/Web of Ideas.png
TryExec=floaters
StartupNotify=false
Terminal=false
Type=Application
Categories=GNOME;Screensaver

does it only work with any specific image type?

---

