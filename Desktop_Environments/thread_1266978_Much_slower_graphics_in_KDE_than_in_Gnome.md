---
title: "Much slower graphics in KDE than in Gnome"
date: 2009-09-15
forum: Desktop Environments
---

### Post by depeha on 2009-09-15
Hi. I have installed Jaunty and using KDE 4.3. Problem is, graphics in KDE is much slower than in gnome... almost 2x! Animations in gnome are smooth and fast, but in KDE are so slow and some doesn't show at all.

Here is glxgears in gnome:
```
matej@matej-laptop:~$ glxgears
Failed to initialize GEM.  Falling back to classic.
890 frames in 5.0 seconds = 177.910 FPS
890 frames in 5.0 seconds = 177.818 FPS
918 frames in 5.0 seconds = 183.447 FPS
891 frames in 5.0 seconds = 178.105 FPS
893 frames in 5.0 seconds = 178.406 FPS
892 frames in 5.0 seconds = 178.264 FPS
892 frames in 5.0 seconds = 178.266 FPS
892 frames in 5.0 seconds = 178.211 FPS
892 frames in 5.0 seconds = 178.326 FPS
889 frames in 5.0 seconds = 177.755 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 27705 requests (41 known processed) with 0 events remaining.
```

in KDE:
```

matej@matej-laptop:~$ glxgears
Failed to initialize GEM.  Falling back to classic.
631 frames in 5.0 seconds = 125.974 FPS
597 frames in 5.0 seconds = 119.359 FPS
477 frames in 5.0 seconds = 95.353 FPS
494 frames in 5.0 seconds = 98.767 FPS
495 frames in 5.0 seconds = 98.804 FPS
534 frames in 5.0 seconds = 106.648 FPS
456 frames in 5.0 seconds = 91.172 FPS
520 frames in 5.0 seconds = 103.968 FPS
487 frames in 5.0 seconds = 97.380 FPS
500 frames in 5.0 seconds = 99.819 FPS
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 16149 requests (41 known processed) with 0 events remaini
```

My laptop specs:
HP Compaq 6720s
Intel Pentium dual core T2410
Intel GMA X3100
2GB RAM

I have also installed [xserver-xorg-video-intel-2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4). Graphics is faster, but still not smooth as in Gnome :confused:

Oh... almost forget... I have used Mandriva 2009 Spring for one week with KDE 4.3, and graphics was as fast as in Ubuntu's gnome.

---

### Post by ianmillington on 2009-09-15
For me KDE 4.3.1 (with desktop effects) is very fast and smooth with a humble Intel 915 (Dell 630m Laptop).

Take a look here.

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

Assuming everything else is Okay, that should go some way to solving your problem.

---

### Post by depeha on 2009-09-15
WOW! :shock::shock:
It's MUCH MUCH MUCH faster! :D
GREAT! 

THX ianmillington :D

---

### Post by ianmillington on 2009-09-15
Great stuff!

To help others would you be good enough to mark your thread as solved?

---

### Post by krazyd on 2009-09-15
I'm glad your issue was solved, but for future reference please note:
[http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark](http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark)

---

