---
title: "[SOLVED] problem with graphics (compiz)"
date: 2008-12-16
forum: Desktop Environments
---

### Post by darijan on 2008-12-16
i think that i need to tell everything from the beginning...

i've installed wine and than "World of Goo" windows game...
after closing game, my screen resolution was small, smth like 800*600.
i went to System>Preferences>Screen Resolution, and i clicked on 1440*900 (tipical resolution for my 19'' wide PR0VIEW monitor). but desktop and icons were strange, and i again went to screen resolution, and tried few different resolutions, and at some resolution (i dont remember what) my monitor was black with "mode not supported" notification. i was stucked, cuz i cannot do any thing... i rebooted pc on button on pc case, and everything with display  was ok (i even heard start up sound) untill it comes to my ubuntu desktop... again same "mode not supported" thing... i rebooted it again and opened recovery mode... i used xfix command there, and then rebooted, and everything was ok. 

everything, *except one thing - compiz*..*. it dont work.*.. i dont have any effect, i dont have cube:sad:

when i go to System>Administration> nVidia X server settings
i get message > You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

i run nvidia-xconfig from terminal, and i dont know how to restart x server...

what should i do?

```

[COLOR="Red"]Edit: I just noticed the "Desktop Effects & Customization" category, which probably is more precise than this category. Sorry for that, I'm new and didn't see it the first time! Please feel free to move this thread[/COLOR]!
```

---

### Post by doobiest on 2008-12-16
issue a glxinfo from the terminal and see if you get something like this

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:

---

### Post by darijan on 2008-12-16
i typed glx info in terminal and i get 

```
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
3 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Segmentation fault

```

---

### Post by doobiest on 2008-12-16
segfault yikes!

you didnt paste the whole output, theres a page or so worth.. you might want to do this instead and just paste the first page

glxinfo| more

---

### Post by darijan on 2008-12-16
man, 

> system > Admin > Hardware driver > re enable video driver 

resolved my problem. thanks for ur help :)

can u help mi with next problem... its similar to this, i think its up to resolution or my lcd monitor
its about games
when i go to "video (or screen) options" menu in any game, and click "play in fullscreen", i get the same  "mode not supported" message.. 
i think that is because games are not made in widescreen mode (i think that the highest resolution in games is 1280*1024)

why does screen blocks when i choose that (lets call it) "irregular" resolution, and i MUST restart my PC.. and after restart when i start game again, screen blocks again so the only thing that i can do is "uninstall game":sad:
 
can i do something?

---

### Post by darijan on 2008-12-31
this one solved,

i need help on

[http://ubuntuforums.org/showthread.php?t=1013669](http://ubuntuforums.org/showthread.php?t=1013669)

---

