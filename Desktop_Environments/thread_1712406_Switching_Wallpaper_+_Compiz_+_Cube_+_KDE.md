---
title: "Switching Wallpaper + Compiz + Cube + KDE"
date: 2011-03-22
forum: Desktop Environments
---

### Post by saphyn on 2011-03-22
Hello all!

I'm looking for a program, script I can run in cron, or anything else that can help me have rotating (time-based) wallpapers, preferably different for each of my desktops but just one would be nice.

I tried Drapes, it seemed to be exactly what I was looking for but A) it didn't work and B) it froze and I had to force kill it every time I went to "General" options.

I'm running Desktop Cube, Rotate Cube, Cube Reflection, 3D Windows, Compiz + Emerald in general on top of KDE. 

If anyone has any ideas, that would be great. I'm completely stumped by this.

Thanks!

---

### Post by saphyn on 2011-03-24
This is actually what I was looking for:

```
#!/bin/bash
pic=/your/background/directory 
newbg="$(ls $pic | shuf -n1)"
dbus-send --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/cube/screen0/skydome_image org.freedesktop.compiz.set string:"$pic$newbg"

```

---

### Post by ankspo71 on 2011-03-24
Hi,
Have you tried the built in wallpaper changer in KDE4?  If you want to try it, right click on your desktop and unlock your widgets. Next, right click on your desktop and choose "desktop view settings" (or folder view settings etc). When the settings window opens up, go to the "View" category on the left, then where it says "Wallpaper:" select "Slideshow" from the dropdown menu.

It is also possible to have separate slideshows for each virtual desktop too. If you want to try this, start by right clicking on the pager widget in your taskbar, then select pager settings, choose the "Virtual Desktops" category on the left, then enable "Different Widgets For Each Desktop". Now each virtual desktop can have its own slideshow - using its own directory of images and other settings. Each virtual desktop can now also have its own separate set of widgets.

I discovered the separate slideshows for each desktop feature after uprading to KDE 4 .6x, but I am pretty sure KDE 4.5x is capable of doing this too. 

Hope this helps.

---

