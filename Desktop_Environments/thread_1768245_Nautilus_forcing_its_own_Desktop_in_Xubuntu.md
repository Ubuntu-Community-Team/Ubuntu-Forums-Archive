---
title: "Nautilus forcing its own Desktop in Xubuntu?"
date: 2011-05-26
forum: Desktop Environments
---

### Post by neu5eeCh on 2011-05-26
I installed Nautilus Elementary in Xubuntu. The problem is that Nautilus insists on starting up its own desktop (overlaying? Xubuntu's desktop). How do I prevent this (without uninstalling Nautilus?). Right now, I can't see my normal desktop, and there are no titlebars. Everything's a mess.

Also: How do I restart the window manager from the command line in Xubuntu?

---

### Post by VCoolio on 2011-05-26
launch nautilus like this: ```
nautilus --no-desktop
```

---

### Post by hhh on 2011-05-26
There's another way which doesn't use --no-desktop, I like it better since you don't have to mess with the Nautilus .desktop file and it's helpful in case you forget --no-desktop or if another program tries to open Nautilus...

You've noticed that if you kill Nautilus it just respawns and takes over the desktop again. In Xfce4 Settings Manager>>Session and Startup>>Session, set Nautilus>>Restart Style to "Never" and then kill Nautilus. While you're there, do the same to Thunar since you'll be using it infrequently and I haven't noticed any dramatic speed decrease from not having the daemon running.

Now run the following 2 commands in a terminal...```
gconftool-2 -s -t bool /apps/nautilus/preferences/show_desktop false &
``````
gconftool-2 -s -t bool /desktop/gnome/background/draw_background false &
```

You can now start Nautilus normally and it won't take over. Do so to get the daemon running and then log out and "Save session for future logins". Nautilus takes a second to open the first time you use it in a session, it's about as fast as Thunar after that.

You can undo the gconf commands by substituting the word false with true.

To change desktop wallpapers, either use Xfce4 Settings Manager>>Desktop or open Thunar, right-click an image and choose "Set as wallpaper".

Hope that helps.

---

### Post by neu5eeCh on 2011-05-26
Thanks HHH. I was out this evening. I'm back now. I was able to reset Nautilus and Thunar to Never, but the window manager doesn't seem to be starting (no titlebars, keyboard shortcuts, etc....) I can't type anything in the terminal or ALT-F2. I can't do squat until I get the window manager working.

**Edit: **I finally was able to get into a terminal by right clicking on the desktop and choosing "Open Terminal Here". From there, I typed XFWM4 (after trying a number of other options). This worked. Now I can try your other directions.

**Edit:** OK... thread marked as solved. Thank you HHH. Everything is back to normal. Phew. How the heck do you know this stuff?

---

### Post by hhh on 2011-05-27
> **VTPoet said:**
> How the heck do you know this stuff?
I've been using Xfce for about a year now, and slowly learning to customize it...mostly trial and error, some help from this and other forums, a bit from the Xfce Wiki...
[http://wiki.xfce.org/](http://wiki.xfce.org/)

I don't bother with the Xfce forum (they didn't even accept my registration, I have no idea why), and I don't use IRC, but you can always try those avenues too. Feel free to PM me with questions, I might not know the answer but it can't hurt. :)

Oh yeah, it's hhh, no affiliation with the wrestler!

---

### Post by TNAFan on 2011-05-27
> **hhh said:**
> Oh yeah, it's hhh, no affiliation with the wrestler!

I was seriously going to get a hold of him and ask if it was.

---

### Post by ohan_g9 on 2011-12-27
> **hhh said:**
> 
You've noticed that if you kill Nautilus it just respawns and takes over the desktop again. In Xfce4 Settings Manager>>Session and Startup>>Session, set Nautilus>>Restart Style to "Never" and then kill Nautilus. 

The problem with that solution is that next time you start Nautilus it comes back with a new PID, and again it has by default auto restart set to "IMMEDIATELY".

**SOULUTION!:**

```
sudo gedit /usr/share/applications/nautilus.desktop
```
In it, change this row:
```
X-GNOME-AutoRestart=**false**
```

(found it at: [https://bbs.archlinux.org/viewtopic.php?id=119254](https://bbs.archlinux.org/viewtopic.php?id=119254) )

---

