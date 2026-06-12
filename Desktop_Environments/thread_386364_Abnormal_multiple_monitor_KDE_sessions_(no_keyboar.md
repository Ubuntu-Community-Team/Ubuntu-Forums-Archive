---
title: "Abnormal multiple monitor KDE sessions (no keyboard/no title bar)"
date: 2007-03-16
forum: Desktop Environments
---

### Post by AhhhooOOo on 2007-03-16
Hi

A few years ago I installed Breezy Kubuntu onto my parent&#8217;s computer (Sempron, Nvidia Geforce4 Ti4200) then a year ago managed to get the TV-Out working with the TV using the nvidia driver. The monitor and TV have separate KDE sessions (two screens in xorg.conf) and work fine, IIRC when I set it up both had identical desktops, same wallpaper, icons, theme and quick launch.

Unfortunately something happened to the TV desktop and it's acting abnormal, the desktop is completely different to the monitor's desktop and all the windows lack a title bar and border. I thought it could be brought back with ALT+F3 and untick No Border except the keyboard doesn't work, instead the keystrokes go to the monitor's desktop. I also cannot click in any text boxes to type anything, for example, the location bar in Konqueror appears to be disabled or doesn't accept any keystrokes. The main desktop is fine.

Main desktop on monitor (1024x768): [http://nisda.net/junk/tvsnap3.png](http://nisda.net/junk/tvsnap3.png) - Main desktop works fine with no problems
TV desktop (800x600): [http://nisda.net/junk/tvsnap1.png](http://nisda.net/junk/tvsnap1.png) - VLC with no title bar
TV desktop (800x600): [http://nisda.net/junk/tvsnap2.png](http://nisda.net/junk/tvsnap2.png) - Cannot type in any of the boxes
xorg.conf: [http://nisda.net/junk/xorg.conf](http://nisda.net/junk/xorg.conf)

Any help would be appreciated.

---

### Post by MindSeVeR on 2007-07-02
Hi All

I have got the same exact problem. I had Kubuntu 6.10 and now 7.04 and the problem is still there in both. No idea what could be. I checked the xorg.conf and it looks fine. I think the problem is related to kwin... but I have no experience in hacking with it. Can someone suggest any reference for a solution?
Thanks
MindSeVeR.

---

### Post by AhhhooOOo on 2007-07-04
This might not be much help but I happened to be testing the TV out on another video card, swapped the cards back and the second desktop magically fixed itself. I'm sure there's a better solution.

---

