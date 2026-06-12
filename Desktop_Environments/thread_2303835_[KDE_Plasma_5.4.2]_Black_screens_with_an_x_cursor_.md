---
title: "[KDE_Plasma 5.4.2] Black screens with an x cursor on all but the first XScreen"
date: 2015-11-21
forum: Desktop Environments
---

### Post by James_Jones on 2015-11-21
Hi all, 

I set up 5 individual x-screens using nvidia-settings. 
On boot-up x-screen 0 shows a KDE-Plasma desktop just fine.

The other 4 x-screens are black. No panels, wallpaper etc. You can move your cursor to them just fine, but it becomes an x and you can't do anything there.

I can launch a window on any of those displays using DISPLAY=:0.1 kate for example places a kate window on X screen 1.

This setup worked just fine in my Kubuntu 14.04 install (I overwrote it completely to start over with 15.10)

Any ideas how to get a plasma desktop on those other xscreens?

I'd rather not use Xinearama, and the default display detection misses two of my displays, (probably because they're on a different gfx card.

Thanks in advance.

---

### Post by James_Jones on 2015-11-21
Another thing I just noticed. When logging in I get all 5 KDE splash screens in Display 0. It's like KDE is making all of the desktops it's just stacking all of them on Display 0?

---

### Post by James_Jones on 2015-11-22
Another update. It's not just KDE. I just did a full reinstall.
1: Installed Nvidia's drivers.
2: Rebooted. Gnome came back up auto-detecting 3 of my 5 monitors.
3: Opened nvidia-settings, setup the displays as individual x-screens.
4: Rebooted and Gnome comes up with a single display. The other displays are active but without a desktop. Can move my cursor to them, but it turns into an X when on those screens.
Running a program with DISPLAY=:0.1 causes the program to load on the target display, so it's active. There's just no desktop/wallpaper/menu etc.

---

### Post by xaositects on 2016-01-18
Were you ever able to get plasma running on the second xscreen? I have the same setup and the same problem. 

For now I've just moved to XFCE since it handles this scenario perfectly, but I'd really like to go back to using KDE one day. 

From what I've read there are issues with dbus when trying to run two plasma sessions at once. Perhaps someone else can chime in here.

---

