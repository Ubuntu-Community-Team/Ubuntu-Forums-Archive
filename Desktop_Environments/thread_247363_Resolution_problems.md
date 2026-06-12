---
title: "Resolution problems"
date: 2006-08-30
forum: Desktop Environments
---

### Post by miller3790 on 2006-08-30
I have a clean install of Ubuntu 6.06 on a dell optiplex gx280. The max resolution i can get is 1024x768. I've downloaded and ran automatix, that didn't help the problem. I'm fairly new to this distro and need someone to point me in the right direction. Any help would be greatly appreciated. Thanks


miller

---

### Post by miller3790 on 2006-08-30
bump

---

### Post by miller3790 on 2006-08-30
so you're trying to tell me that i'm the only person in the world that has ubuntu on a optiplex gx280?

---

### Post by acorn22 on 2006-08-30
Well, I cant help you, but I have the same problem. 

cept I'm not using a dell, I have an ATI Rage Pro II card

---

### Post by CatKiller on 2006-08-31
> **miller3790 said:**
> I have a clean install of Ubuntu 6.06 on a dell optiplex gx280. The max resolution i can get is 1024x768. I've downloaded and ran automatix, that didn't help the problem. I'm fairly new to this distro and need someone to point me in the right direction. Any help would be greatly appreciated. Thanks
By default, X/Gnome/Ubuntu only includes fairly conservative modes rather than polling the hardware directly, as far as I can tell. To enable higher resolutions, there are a couple of steps, the first being of critical importance.

Check your monitor documentation for supported modes. Incorrect settings may well permanently damage your monitor.

Make a backup of your config file:```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
Edit your config file:```
gksudo gedit /etc/X11/xorg.conf
```
Find the line about your monitor and add the modes that you want to the Modes lines for each bit depth. You should be able to see the format from what's there already.

Save the file.

Restart X (Ctrl-Alt-Backspace, by default).

If it works, Ubuntu should start in the highest mode listed. If you've broken it so that it doesn't start, get to a terminal and type ```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
``` to get it back to how it was.

---

