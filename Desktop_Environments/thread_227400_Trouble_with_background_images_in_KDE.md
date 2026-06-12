---
title: "Trouble with background images in KDE"
date: 2006-08-01
forum: Desktop Environments
---

### Post by ousooner919 on 2006-08-01
Hey to all,

I'm running Kubuntu, and try as I might I can't get the background images on any of the 4 virtual desktops I run to change to what I want. In fact, I can't change colors or anything with any of the backgrounds. I've tried applying a new image, even stock images; I've tried changing the color from the standard blue to red...nothing. Even after restarting X and KDE, still no change.

I'm using the "Desktop" part of the  "System Settings" applet in the KDE menu to try to make the change. If I can't get this to work, is there a way I can do it manually in config files or something? Or is there a way I can fix the applet so it actually does what it's supposed to do?

Thanks for your assistance.

---

### Post by neoeden on 2006-08-01
On the systems settings applet, you are selecting desktop, background from the left correct? When you select a different backgroud, are you hitting apply?

---

### Post by ousooner919 on 2006-08-02
Yep, System Settings, Desktop, Background. I select an image, any image, and click apply or OK or apply then OK) and get nothing. Background stays completely unchanged. Same with trying to change colors (for testing). Also doesn't matter if I try for individual desktops or all desktops. This little sub-applet appears to be completely non-functional, though others (Screen Saver, Multiple Desktops, etc.) have no issues.

---

### Post by ousooner919 on 2006-08-17
Found a partial solution to my problem. Ran the following command:

dcop kdesktop KBackgroundIface setWallpaper <wallpaper graphic file> 1

and that put the file in place. Now, if I can just find a way to get different files onto each desktop background...

Still EXTREMELY disappointed that I can't get that applet to work properly. Oh well, it's not as though the magic KNetworkManager has worked for my WPA-based home WiFi network at all, either...  :sad:

---

### Post by Linux4HumanBeings on 2006-08-17
Also, Make sure when you set something as your desktop background you leave it in the same folder orplace beacuse if you move it your background will disappear after a reboot.

---

