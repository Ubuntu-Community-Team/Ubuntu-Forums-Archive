---
title: "Display wall weirdness -- help!"
date: 2008-07-31
forum: Desktop Environments
---

### Post by blorch on 2008-07-31
Hey everyone. I'm working on a project for my school involving 16 monitors working together as one unified display. I have four backend machines (named floyd1-4) driving four monitors each, and one frontend box (bender) for running applications. 

I'm using DMX with Chromium to make this work. The DMX setup is working great for the most part; I can start a session, I can move the mouse around all the monitors, launch applications, etc. It's just a little slow because DMX isn't designed to handle such a large display wall unaided. This is where the Chromium comes in. I created my Chromium config files using [this setup]("http://www.rossmanaudio.com/switcher/sample1/DisplayWall.html") as a rough guide (I can post my own versions upon request, but I didn't want to drown this post in code).

The Chromium documentation also calls for creating these links:

<chromium>/lib/Linux/libGL.so -> <chromium>/lib/Linux/libcrfaker.so
<chromium>/lib/Linux/libGL.so.1 -> <chromium>/lib/Linux/libcrfaker.so

and setting LD_LIBRARY_PATH to <chromium>/lib/Linux. If everything goes well, any OpenGL application should then automatically start a Chromium mothership, start servers on the backend machines, and run the app in parallel.

As far as I can tell, most of this seems to be working. However, when I try running something like glxgears, I get the following output:

```
umcs@bender:~/Desktop$ glxgears
CR Warning(bender:30085): the OpenGL faker was loaded without crappfaker!
Defaulting to an application id of -1!
This won't work if you're debugging a parallel application!
In this case, set the CR_APPLICATION_ID_NUMBER environment
variable to the right thing (see opengl_stub/load.c)
CR Warning(bender:30085): Using Chromium configuration for * from /home/umcs/.crconfigs
Chromium autodmx.conf: using ~/.crsite
This is Chromium, Version 1.9
Autostart for node floyd1: ['/usr/bin/rsh', 'floyd1', "/bin/sh -c 'DISPLAY=:0.0  LD_LIBRARY_PATH=/home/umcs/src/cr-1.9/lib/Linux  crserver -mothership bender:10023'"]
Autostart for node floyd2: ['/usr/bin/rsh', 'floyd2', "/bin/sh -c 'DISPLAY=:0.0  LD_LIBRARY_PATH=/home/umcs/src/cr-1.9/lib/Linux  crserver -mothership bender:10023'"]
Autostart for node floyd3: ['/usr/bin/rsh', 'floyd3', "/bin/sh -c 'DISPLAY=:0.0  LD_LIBRARY_PATH=/home/umcs/src/cr-1.9/lib/Linux  crserver -mothership bender:10023'"]
Autostart for node floyd4: ['/usr/bin/rsh', 'floyd4', "/bin/sh -c 'DISPLAY=:0.0  LD_LIBRARY_PATH=/home/umcs/src/cr-1.9/lib/Linux  crserver -mothership bender:10023'"]
Start a crappfaker on bender
Mothership signalling spawning process 30085
CR Info(floyd1:13915): Total output dimensions = (1100, 1100)
CR Info(floyd2:10514): Total output dimensions = (1100, 1100)
CR Info(floyd3:8196): Total output dimensions = (1100, 1100)
CR Info(floyd4:12780): Total output dimensions = (1100, 1100)
glxgears: ../../src/xcb_io.c:453: _XRead: Assertion `dpy->xcb->reply_consumed + size <= dpy->xcb->reply_length' failed.
Aborted
```

I haven't found mention of this exact assertion failure anywhere. Does anyone know what's going on here? I feel like I'm really close to getting it working, but this has been driving me crazy!

---

