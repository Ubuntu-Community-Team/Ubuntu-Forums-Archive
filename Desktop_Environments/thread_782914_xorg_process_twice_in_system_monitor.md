---
title: "xorg process twice in system monitor"
date: 2008-05-05
forum: Desktop Environments
---

### Post by matoxxx on 2008-05-05
hello, 

i d like to ask if its normal to have 2 identical xorg processes running at the same time, just with one difference, one is consuming cpu, another not.

my xorg.conf
[HTML]Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"sk"
	Option		"XkbVariant"	"qwerty"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection[/HTML]


i am running Hardy+gnome+compiz-fusion with Express200+fglrx-driver up to date

---

### Post by magnusbb on 2008-05-05
I have the same issue.

My earlier (unanswered) post:
[http://ubuntuforums.org/showthread.php?t=777053](http://ubuntuforums.org/showthread.php?t=777053)

Another post on this issue:
[http://ubuntuforums.org/showthread.php?t=465435](http://ubuntuforums.org/showthread.php?t=465435)

Installing a newer version of the fglrx-driver did not work.

---

### Post by matoxxx on 2008-05-06
Ah, OK this should be some kind of bug. downgraded to gutsy, and still two xorg processes appearing. Turning off the compiz and xgl resolves in no RAM usage by these two processes, turning them on gets same problem.

How can i get some evidence to prove memory leak either by compiz or fglrx ?

PS: just to comparison, compiz on cca 300MB RAM usage, compiz off 120MB RAM usage

---

### Post by matoxxx on 2008-05-06
Hmm, okey problem unsolved by updating the drivers, i am now using binary 8.46 driver and issues still present.

---

### Post by magnusbb on 2008-05-06
When I switch from the proprietary ATI driver to the VESA driver, the problem disappears. No doubt where the problem lies. 

Are we the only ones experiencing this, or is a double xorg process the case for every user of the commercial driver? Can someone confirm that?

---

### Post by smif1984 on 2008-05-06
I had the same problem until five minutes ago, when i booted in root mode. Then a text menu appeared  to let me choose from logging in as root, reboot the system or fixing the X server. Well, i did it, and now i don t have anymore these two Xorg processes. That s luck. 
\\:D/

---

### Post by matoxxx on 2008-05-07
Sorry to tell, you, this is not the solution, repairing x will just overwrite your xorg.conf file to use build-in open source ati driver, if you want to stick with fglrx and 3D support you have to find another solution.

I will try to contact ati-amd support team for answers

---

### Post by bigbig on 2008-05-07
haaaaaaaaaaaaay

---

### Post by matoxxx on 2008-05-07
When i will have time, i will try do downgrade the ati drivers to least possible, if the problem still persis it has to be Xorg 7.3 problem.

stay tuned for results

---

### Post by ferchon03 on 2008-05-07
I've the same issue.
```
fer@fer:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 PRO
OpenGL version string: 2.1.7412 Release

```

---

### Post by matoxxx on 2008-05-10
Ok now running Gutsy with restricted ati driver

[PHP]fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6473 (8.37.6)[/PHP]

[PHP] glxinfo | grep render
direct rendering: Yes
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: ATI Radeon Xpress Series[/PHP]

with following error
[PHP](EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)[/PHP]

which concludes to known bug, where fglrx hates aixgl = i hate fglrx
I have tried to stick with new mesa update, which should work with my Xpress 200M, but no way in my case.

I came to point i not willing to spend more of my time with this and i am dissapointed of ati once again. I will not buy any ati product anymore and my advice you do so too.

---

### Post by bigbig on 2008-05-10
mmmmmmmmmmmmmmmmm

---

### Post by bigbig on 2008-05-10
mmmmmmmmmmmmmmm

---

### Post by macduy on 2008-06-17
Hi, I'm experiencing the same problems, was just wondering if anyone has found a fix yet. 

Been googling around but not much found

---

### Post by ferchon03 on 2008-06-17
> **macduy said:**
> Hi, I'm experiencing the same problems, was just wondering if anyone has found a fix yet. 

Been googling around but not much found

Me too, i'm still having this issue since I've installed Hardy Heron.

---

### Post by yarik on 2008-09-02
I'm also can confirm such behavior with ati drivers.

---

### Post by Goombie on 2008-09-02
Interestingly enough, I have NO xorg processes running at this time. I should note that I have the open source ATI drivers, so this sounds like it might be a problem with the closed-source ATI drivers.

---

### Post by ScarySquirrel on 2008-09-26
I have the same problem, and I use the fglrx driver.
     My Gnome System Monito lists two Xorg Processes.  
     Also, my Gnome System Monitor reports memory allocation far in excess of the sum total of all listed processes, regardless.

---

