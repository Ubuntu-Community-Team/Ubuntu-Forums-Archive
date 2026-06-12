---
title: "Compiz Is Slow For Me"
date: 2008-03-08
forum: Desktop Effects &amp; Customization
---

### Post by Brando569 on 2008-03-08
compiz 0.7 is lagging a decent amount for me and it definitely shouldnt be. i have an amd 64 x2 6400 black edition, 2gb ddr2 ram, raptorX 150gb sata 2 hdd, and a geforce 8600 GTS OC. kwin runs flawlessly, yet compiz will lag when i minimize/maximize windows, when i draw gestures with firefox, when i resize windows, etc.. i also have the restricted drivers installed, so that should be the problem. i dont know if this will help but heres the output when i launch compiz from a terminal:

```
brandon@ra:~$ compiz --replace
Checking for Xgl: not present.
Detected PCI ID for VGA: 03:00.0 0300: 10de:0400 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1680x1050) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present.
Checking for FBConfig: present.
Checking for Xgl: not present.
Starting emerald
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
inotify_add_watch: No such file or directory

```

also how can i make it so that a window will gain focus when i mouse over it? to bring a window in the background to the foreground i have to click on the title bar which is kind of annoying, id like to be able to click anywhere on the window and have it be brought to the front.

---

### Post by buckeyered80 on 2008-03-08
I am having a very similar problem.  Compiz works on mine, but it is just way too slow when minimizing and resizing windows.  Also on the scroll, it lags bad on certain applications.  On Ubuntu 7.10, my compiz worked fine.  This problem seems to be on Kubuntu with ATI drivers...possibly.  I am not totally sure.  I am researching the issue, I'll let you know if I find anything.

---

### Post by Brando569 on 2008-03-08
i think its just a general problem with compiz 0.7 because im using nvidia drivera

---

### Post by 22flames on 2008-03-08
no its not general but have you tried going into the CCSM manager and goging to opcity and click on the raise on mouse over button. ps. I would try to installe xgl from the snaptic and i have 512 ram with old nvidia gforce and compiz 0.7 with restriced drivers and it runs like a dream its not a general prob

---

### Post by buckeyered80 on 2008-03-08
Do you have xserver-xgl installed?  You can get it via synaptic.  Or just:

sudo apt-get install xserver-xgl

---

### Post by Brando569 on 2008-03-24
i just installed xserver-xgl and that seemed to fix it, thanks. opacify isnt exactly what i wanted but it works for what i want

---

