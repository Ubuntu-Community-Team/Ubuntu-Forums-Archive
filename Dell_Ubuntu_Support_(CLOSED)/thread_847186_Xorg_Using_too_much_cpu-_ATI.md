---
title: "Xorg Using too much cpu- ATI"
date: 2008-07-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sayantandas on 2008-07-02
Hi,
I am using Ubuntu 8.04 on dell inspiron 6400. I have installed watermarks screenlets to see my cpu usage. It shows me my cpu usage is very high all the time. even if i am not using the system , the cpu usage is between 45-50% . and the xorg using the most cpu on the top ten processes list. can anyone suggest a solution?

My comp specs:
_Inspiron 6400_

cpu: core 2 duo t5200 @ 1.6mhz
ram: 2048 mb
graphics card: ati x1400 hypermemory
ubuntu 8.04 kernel : 2.6.24-19

---

### Post by sayantandas on 2008-07-03
i fixed the issue by reinstalling ati catalyst centre from amd site
but now i seem to have a new problem
surfing through the forum i saw users having a framerate of a min 1000FPS. where as my FPS is coming to 45-50 FPS... any explanation for this?
here are the details

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.1.7659 Release

glxinfo | grep rendering
direct rendering: Yes

243 frames in 5.0 seconds = 48.570 FPS
295 frames in 5.0 seconds = 58.960 FPS
295 frames in 5.0 seconds = 58.853 FPS
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 1152 requests (1151 known processed) with 0 events remaining.

and i get this wired error message once i close the gears. what can be the problem?

---

### Post by sayantandas on 2008-07-03
edit:

i re-installed ati drivers again using the wiki at
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.6.29](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.6.29)
now i'm getting a better FPS without errors
~$ glxgears
12091 frames in 5.0 seconds = 2418.151 FPS
12667 frames in 5.0 seconds = 2533.292 FPS
12251 frames in 5.0 seconds = 2450.167 FPS
12384 frames in 5.0 seconds = 2476.798 FPS
12582 frames in 5.0 seconds = 2516.294 FPS
12468 frames in 5.0 seconds = 2493.500 FPS
12436 frames in 5.0 seconds = 2487.057 FPS
12413 frames in 5.0 seconds = 2482.412 FPS
11671 frames in 5.0 seconds = 2334.027 FPS
12090 frames in 5.0 seconds = 2417.866 FPS
12503 frames in 5.0 seconds = 2500.534 FPS

~$     DISPLAY=:0 glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: ATI Mobility Radeon X1400

---

