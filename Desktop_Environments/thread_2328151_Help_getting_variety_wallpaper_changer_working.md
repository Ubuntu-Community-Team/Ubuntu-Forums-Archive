---
title: "Help getting variety wallpaper changer working"
date: 2016-06-17
forum: Desktop Environments
---

### Post by lsutiger on 2016-06-17
I discovered Variety today while looking for a desktop wallpaper changer for my work computer. I really like it and wanted to get it working on my home computer, but or some reason it is not working. Here are the details:
On my work computer I am running 14.04 with a gnome fallback metacity. On the home computer, same version and I have gnome fallback compiz. On the home computer at one time I did have the wallpaper utility from the ccsm turned on. When I go to the System Settings-->Appearance and change the background there, the desktop background does not change. And after setting up variety it does not work. 
Any pointers on what to check?

---

### Post by CantankRus on 2016-06-20
Terminal...
```
gsettings get org.gnome.desktop.background show-desktop-icons
```
If it returns "false",  run ...
```
gsettings reset org.gnome.desktop.background show-desktop-icons
```

---

### Post by lsutiger on 2016-06-22
The first command returned false, so I ran the second command. Nothing changed. Some more information: The login background is the same as the desktop wallpaper and has been for quite some time(1 yr+) and I believe I edited some file to make that happen. I used grep in an attempt to find the filename in a file but the search ended up being fruitless. I did check in the dconf-editor and noticed that the value for org-->gnome-->desktop-->background-->pictureuri matches what the variety wallpaper changer should be displaying on my desktop.

---

### Post by CantankRus on 2016-06-22
Yeah I don't know really if you edited some file but can't remember which one.
Nautilus handles the desktop and should be in startups under "Files" with the command being "nautilus -n".

Something that might help you is you can monitor changes in dconf with the command...
```
dconf watch /
```
Say I change my desktop background it will show the dconf changes as in pic.

---

### Post by lsutiger on 2016-06-22
Thanks. Will do!

---

