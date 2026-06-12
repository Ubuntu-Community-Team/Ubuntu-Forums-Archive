---
title: "Can't get past login screen in 10.04"
date: 2010-09-09
forum: Desktop Environments
---

### Post by lbmounse on 2010-09-09
I am trying to get Kubuntu 10.04 to work.

When I install it on this PC, it works up to the login screen.  When I login,  it acts as if it were logging in.  But then it takes me back to the login screen.  

Ubuntu 10.04 works fine on this PC, but I prefer KDE.  

Could this be a problem with the graphics card?
It is a cheap onboard one, and I can't even use the 
basic desktop effects in Ubuntu (gnome)

---

### Post by syano on 2010-09-11
I know, this sounds stupid, but I've had people do it before: did you enter the correct username and password?
 
If you did, I have a question.  Are there any other operating systems on  your computer, or did you do a clean install of Kubuntu on the system?  I don't think the graphics card would have anything to do with it.  Perhaps burn another disc of Kubuntu and try installing again if you have time.

---

### Post by lbmounse on 2010-09-12
It can't be the password, because I'm currently logged in to GNOME on the same computer.

It is a dual boot with win XP.  It has both GNOME and KDE installed, I can get into GNOME, but not KDE.  Previously, it had Ubuntu 8.04.  I did a complete reinstall because the upgrade failed.  

I even tried installing Kubuntu in windows via wubi, but it still has the same problem.

---

### Post by lbmounse on 2010-09-12
I found the solution here:
[http://ubuntuforums.org/showthread.php?t=1462745&page=2](http://ubuntuforums.org/showthread.php?t=1462745&page=2)


> Add to the .kde4/share/config/kwinrc (.kde/share/config/kwinrc)

[Compositing]
Enabled=false
Last edited by metrofun; July 7th, 2010 at 10:33 AM.. 


This will force desktop effects off, for those with old/cheap graphics cards.

---

### Post by oradano on 2010-11-24
thanks all,
 
I just wanted to piggy-back on this in case anyone ran into the same issue
 
I just upgraded 10.04 to 10.10, then installed kubuntu-desktop.  kde started locking up and gnome (Ubuntu desktop) started but without the panel I'd setup (long after deleting the default one).
 
Anyway this fix resolved the issue, alot easier than re-installing another destop.
 
Much appreciated!:popcorn:

---

