---
title: "Desktop Wallpapers"
date: 2016-09-10
forum: Desktop Environments
---

### Post by DeadlyOats on 2016-09-10
What is the path to the folder where wallpapers are saved? I'm using Kubuntu 16.04.

---

### Post by howefield on 2016-09-10
Try..

```
/usr/share/backgrounds
```

---

### Post by DeadlyOats on 2016-09-11
Thanks for your reply, but it seems I don't have /usr/share/backgrounds.  I found a /usr/share/wallpapers, but it only had the default wallpaper that comes with the install.  I've been using the Desktop Settings utility to "Install" more wallpapers.  I can't find the folder those wallpapers have been "installed" to.

---

### Post by vasa1 on 2016-09-11
> **DeadlyOats said:**
> Thanks for your reply, but it seems I don't have /usr/share/backgrounds.  I found a /usr/share/wallpapers, but it only had the default wallpaper that comes with the install.  I've been using the Desktop Settings utility to "Install" more wallpapers.  I can't find the folder those wallpapers have been "installed" to.What is the source of these wallpapers you've installed? Where have you obtained them from?

---

### Post by howefield on 2016-09-11
> **DeadlyOats said:**
> Thanks for your reply, but it seems I don't have /usr/share/backgrounds.  I found a /usr/share/wallpapers, but it only had the default wallpaper that comes with the install.  I've been using the Desktop Settings utility to "Install" more wallpapers.  I can't find the folder those wallpapers have been "installed" to.

Ah ok, in that case try navigating to the following folder in /home..

```
/home/hugh/.local/share/wallpapers/
```

obviously substituting your own username.

---

### Post by DeadlyOats on 2016-09-12
Thanks, howefield! That's what I needed!  I had to Click on the "Control" button on Dolphin's menu bar, and then click on "Show Hidden Files" to display the .local folder, but then I found it.  Thanks!  Now I've set up the "Slideshow" option for my desktop, and all of those nice wallpapers are cycling on my desktop!

Again, my thanks!

---

### Post by howefield on 2016-09-12
Cool, you are welcome, thanks for marking the thread solved.

---

