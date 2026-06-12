---
title: "Desktops/Wallpapers"
date: 2008-01-28
forum: Desktop Effects &amp; Customization
---

### Post by durdensbuddy on 2008-01-28
I tried to add different wallpapers to each desktop by downloading the images and then typing their locations into ccsm but desktop did not change.  When i used appearance, Ubuntu saw one of the files and I was able to apply that as a wallpaper, however it is now on all four sides of my cube.  Also, all of the wallpapers came from gnome-look.org

Also, I haven't been able to modify my display resouloution.  I have enabled my restricted drivers for NVidia card, but on earlier installs (this is #4, too much playing in the terminal + too little knowledge = bad) I had a drop-down menu of display options now i get this:

/home/shannon/Desktop/Screenshot-CompizConfig Settings Manager.png

Running Gutsy 7.10

---

### Post by squab on 2008-01-29
You can change the resolution setting in the nvidia driver config menu.

```
gksudo nvidia-settings
```

don't forget to output your X configuration file at the bottom of the menu and log in again afterwords

---

