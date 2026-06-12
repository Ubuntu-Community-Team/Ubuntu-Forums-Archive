---
title: "Xubuntu has garbage on desktop background layer"
date: 2007-05-11
forum: Desktop Environments
---

### Post by shaunandmarie on 2007-05-11
I just installed Xubuntu and it is delightfully snappy -- especially after going through all the HOWTO's on maximizing Ubuntu performance.

However, after running programs such as Firefox, I get garbage on the desktop background layer (beneath the icons but in front of the wallpaper) that is a graphical portion of a window I had just opened.  At this point, I am only able to remove it by make some change to the desktop settings' background display -- this seems to refresh it (changing wallpaper, color selection).  See screenshot attached.

---

### Post by bapoumba on 2007-05-11
Hello, did you enable compositing?

---

### Post by shaunandmarie on 2007-05-11
At some point, I did enable compositing after the fact of it occuring, and it happened again.  Right now, its not enabled.

---

### Post by bapoumba on 2007-05-12
So what video card and drivers are you using?
(I do not know much about video, but others do over here).

---

### Post by shaunandmarie on 2007-05-12
Vendor S3 Inc.
Device VT8375 [Prosavage8 KM266/KL266]

---

### Post by bapoumba on 2007-05-12
On this older laptop, I have a prosavage KM266 too.
Have you run (in a terminal)? :
```
sudo dpkg-reconfigure xserver-xorg
```
Keep the default answers if you do not know. To select an item, use the <space> and put a * (in the resolutions you want to use for ex).
It detected automatically the savage card and used the savage driver.
resart X with CTRL-ALT-Backspace.

---

### Post by dsegarra on 2007-05-12
shaunandmarie,
I love ubuntu, dont get me wrong it is my fav distro. But if you want to try a really good XFCE distro and Ubuntu is just not working, try Zenwalk. I am a new, big fan of Zenwalk. Its stable, fast and it has all worked for me.

---

### Post by shaunandmarie on 2007-05-14
I attempted

sudo dpkg-reconfigure xserver-xorg

immediately and decided to wait about 24 hours before responding (as the problem occuring somewhat intermittently).  It seems that the problem is no longer recurring.  Thank you!

Regarding Zenwalk:  At the beginning of this problem, I researched what the best distro. implementing the XFCE desktop would be and found that Zenwalk would be the most desirable next choice.  I have an ISO burned and ready but am too happy with Xubuntu at this point!

---

### Post by bapoumba on 2007-05-14
Glad to see you got it to work.

---

