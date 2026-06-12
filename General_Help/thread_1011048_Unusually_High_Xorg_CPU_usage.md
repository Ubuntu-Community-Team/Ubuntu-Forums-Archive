---
title: "Unusually High Xorg CPU usage"
date: 2008-12-14
forum: General Help
---

### Post by damis648 on 2008-12-14
Hey,
for some reason ever since yesterday Xorg's CPU usage has been usually high, in general as well as when holding down a key in a text editor and moving windows, etc. Top shows the following:
```
 7482 root      20   0  110m  60m  14m S   11  1.7  11:48.26 Xorg               
 7635 damian    20   0  406m  96m  24m R    9  2.7   0:29.82 firefox            
10718 damian    20   0 92512  60m  28m S    6  1.7   2:24.13 compiz.real        
 9617 damian    20   0  356m  30m  10m S    3  0.9   1:25.83 transmission       
 8178 damian    20   0  177m  14m 9516 S    1  0.4   0:16.32 sensors-applet     
 8244 damian    20   0 11500 2332 1364 S    1  0.1   0:40.96 conky              
 8430 damian    20   0  265m  40m  13m S    1  1.1   0:16.92 gnome-terminal     
 2301 root      15  -5     0
```

and goes up to 28% when moving a window or doing something of the sort. Any ideas? Disabling compiz does nothing, and stopping gnome-settings-daemon doesn't do anything either. I can't find anything relevant in Xorg.0.log. Yesterday I did the following:
```
Upgraded the following packages:
compiz-fusion-plugins-main (0.7.8-0ubuntu2.1) to 0.7.8-0ubuntu2.2
libgnutls26 (2.4.1-1ubuntu0.1) to 2.4.1-1ubuntu0.2
vinagre (2.24.1-0ubuntu1) to 2.24.1-0ubuntu1.1

Installed the following packages:
hfsplus (1.0.4-12build1)
hfsutils (3.2.6-11build1)
libhfsp0 (1.0.4-12build1)
```
 Thanks in advance!

---

### Post by damis648 on 2008-12-14
I will marked this as solved. I installed the 180.06 beta nVidia driver which seems to have minimized the symptoms.

EDIT: Marking as unsolved, CPU usage is still way too high.

---

