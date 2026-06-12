---
title: "Desktop resolution and GUI error"
date: 2009-08-08
forum: Desktop Environments
---

### Post by zomgneeks on 2009-08-08
Hi

After installing Sun VirtualBox and windows xp. I had windows open in virtualbox when I closed my laptop. When I opened it, the display was frozen. I pressed ctrl+alt+f1 and typed ```
sudo halt
```When I booted up again, the ubuntu login screen was cropped so only part of the screen was being displayed. The text "User name" and "password" was not shown although I could log in.

Once logged in, my resolution was 640x350. I was able to change it to 1024x768 but I usally run at 1200x800.

The screenshot attached does not capture my full screen. My wallpaper repeats rather than filling the screen. When I left click on the desktop and drag past the edge of where the screenshot ends the box does not follow. I cannot start a box outside of the area in the screenshot

Maximize does not fill the screen. In the screenshot I have mozzila maximized. The top of the box is about halfway on my screen and the bottom is almost touching the bottom panel.

On the top pannel the bluetooth applet, power management and wicd tray icons are farthest to the right rather than the volume applet, clock, and Fast User Switch Applet.

On the bottom tray the trash tray icon is about 2/3rds across the screen and the Workspace Switcher is farthest to the right.

In the workplace switcher, it only displays the windows that are within the screenshot's area. So if I were to bring a window under that area it would not be on the workplace switcher tray.

I tried
```
sudo apt-get install --reinstall ubuntu-desktop
```but that did not fix anything


What have I done?!

---

### Post by zomgneeks on 2009-08-09
Problem solved.

First I did 
```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```
to reset gnome.

then
```
sudo dpkg-reconfigure xserver-xorg
```
to get the resolution back to normal.

This bug was horrifying. I've never seen so many things break at the same time.

---

### Post by bobmendon on 2009-08-09
Good show! I was thinking it was an xorh issue and you found it right away!

---

### Post by zomgneeks on 2009-08-09
Actually, there is still one small problem. When I log in tray icons get shuffled around [I]sometimes.

[/I]I think I'll just switch. What's a good minimalist GUI? Openbox?

---

### Post by SoftwareExplorer on 2009-08-09
niko.stap, nice background. Is there somewhere where I can get it?

---

### Post by zomgneeks on 2009-08-09
Here. And some related too.:)

---

### Post by SoftwareExplorer on 2009-08-10
> **niko.stap said:**
> Here. And some related too.:)
Nice. Did you make them? If so, I would say the fourth would look good with colors like the first, for example, less pastel, more full-strength colors without white or black added. Still nice though. Thanks :)

---

### Post by zomgneeks on 2009-08-22
> **SoftwareExplorer said:**
> Nice. Did you make them?

I wish! I found them on various #chan wallpaper boards

---

