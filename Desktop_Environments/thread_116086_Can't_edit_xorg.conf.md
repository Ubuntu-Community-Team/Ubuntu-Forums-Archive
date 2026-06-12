---
title: "Can't edit xorg.conf"
date: 2006-01-11
forum: Desktop Environments
---

### Post by Razorback on 2006-01-11
I found a post that talked about editing the video settings by the xorg.conf.  I have been getting some weird video glitches.  I will sometimes see a bar pattern on the window displays.  It was mentioned to check the xorg.conf.

I used:  sudo gedit /etc/x11/xorg.conf

It launched gedit but xorg.conf opens up empty.  If I use Nautilus I can see the file but cannot edit it.  Any help would be appreciated.

---

### Post by astoltz on 2006-01-11
I think the path should be /etc/X11/xorg.conf - note the capital X.  Linux is case sensitive.

---

### Post by Pixel on 2006-01-11
[QUOTE=Razorback]I found a post that talked about editing the video settings by the xorg.conf.  I have been getting some weird video glitches.  I will sometimes see a bar pattern on the window displays.  It was mentioned to check the xorg.conf.

I used:  sudo gedit /etc/x11/xorg.conf

It launched gedit but xorg.conf opens up empty.  If I use Nautilus I can see the file but cannot edit it.  Any help would be appreciated.[/QUOTE]

Linux is strictly case-sensitive.

The reason why it isn't working is becuase you typed:
```
sudo gedit /etc/x11/xorg.conf
```
when you needed to type:
```
sudo gedit /etc/X11/xorg.conf
```
But if you wish, you can get access to the file by starting Nautilus in root-mode by typing:
```
sudo nautilus
```

---

### Post by Razorback on 2006-01-11
I guess I should learn to type! :p Changed the x11 to X11 and it worked.  Thanks!  I guess I have been living in the Windows world too long.

---

