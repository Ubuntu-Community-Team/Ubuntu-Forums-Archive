---
title: "[SOLVED] No video acceleration after compiz uninstall"
date: 2008-12-28
forum: General Help
---

### Post by oopsdude on 2008-12-28
Hi all,

I'm running 8.10 Intrepid with kernel 2.6.24-19 on a laptop with an nVidia GeForce Go 6150 card and 4GB of RAM. Gnome is my display manager. After uninstalling compiz and reverting back to metacity, video acceleration has stopped working. (There were graphical glitches with compiz, if it's relevant.) I've tried deactivating and reactivating the restricted driver under System -> Administration -> Hardware Drivers, as well as reinstalling nvidia-glx-177. nvidia-settings shows everything is fine. I also deleted my xorg.conf and regenerated it with nvidia-xconfig without success. I saw the restricted drivers bug in the sticky at the top of this forum, but the workaround was what I'd already tried.

So far, I can't enable any visual effects in the window manager (System -> Preferences -> Appearance -> Visual Effects is greyed out) and Totem locks up and displays a black screen when I try to play a movie. Totem worked fine when compiz was installed. On the other hand, the astronomy program Stellarium renders the same as before, and my old 3D games like Tribes under Wine are also fine. I don't have much else graphically-intensive to test, since it's not a powerful card in the first place. I tried Google Earth, and the edge of the Earth looks a bit blocky when zoomed in, but I don't remember if that happened before. My resolution is still at 1280x1024.

Thanks a lot in advance! I appreciate any help.

Mike

---

### Post by gettinoriginal on 2008-12-28
Try in terminal:

```
 metacity --replace 
```

---

### Post by oopsdude on 2008-12-28
Gnome "refreshes" and then looks exactly the same. However, Totem will now display movies, although without sound. And it locks up again if I adjust the volume. And Rhythmbox locks up in the same way Totem did when I try to play an mp3. Thanks for the reply!

---

### Post by gettinoriginal on 2008-12-28
This is a great troubleshooting site for video and sound:  :P

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by oopsdude on 2008-12-28
So basically you're recommending a reinstall? Because I have every package that FAQ wants, and my system was set up just dandy. I had video acceleration; I had sound; I even had my tablet working. Then I uninstalled compiz, and everything fell apart. I'd just rather not reinstall my entire system because I removed a window manager. :-)

---

### Post by gettinoriginal on 2008-12-28
No no, not recommending a reinstall.  But since you have made changes to your system, you might try logging out, then at the login screen, options, session, gnome, see if that helps at all.

---

### Post by oopsdude on 2008-12-29
Well, I just installed Xcfe as my display manager and that fixed it. Reinstalling the gnome package did nothing. Thanks anyway!

---

