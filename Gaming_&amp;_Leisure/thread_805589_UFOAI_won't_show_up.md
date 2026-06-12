---
title: "UFOAI won't show up"
date: 2008-05-24
forum: Gaming &amp; Leisure
---

### Post by zfolwick on 2008-05-24
so I ran: "sudo ufoai-2.0-rc5-linux.run and got the thing to supposedly install and now it's not showing under applications>games.

I don't get it! 

from the last lines of Terminal:

zach@zach-laptop:~/Desktop$ ./ufoai-2.0
bash: ./ufoai-2.0: No such file or directory
zach@zach-laptop:~/Desktop$ ./ufoai-2.0-rc5-linux
bash: ./ufoai-2.0-rc5-linux: No such file or directory
zach@zach-laptop:~/Desktop$ 


do I need to change from ~/Desktop to something else?  I didn't create a symbolic... . something or other, but the first time I did, it didn't seem to make a difference.

Any advice?  I've got a host of other applications I'd like to add as well (more useful) and am having troubles with the add/remove programs software.

---

### Post by Perfect Storm on 2008-05-24
It's just **ufo** in the terminal.

[http://gaming.gwos.org/doku.php/guides:64bit:ufo_alien_invasion](http://gaming.gwos.org/doku.php/guides:64bit:ufo_alien_invasion)

---

### Post by zfolwick on 2008-05-24
I'm not understanding. . . it's just "ufo"?  As in ./ufo?

---

### Post by Perfect Storm on 2008-05-24
It's just **ufo**

if you use **./ufo** means that you are executing a binary/script at your current directory.

---

### Post by zfolwick on 2008-05-24
ok. . . I tried something else: ufoai-2.2.1-linux.run.

Seems to unpack in the home folder, but now when i click on the icon, nothing happens.  Running from the command line gives this:

> ------- Loading ref_glx.so -------
LoadLibrary("ref_glx.so"): can't open /etc/ufo.conf - setting search path to .
LoadLibrary("ref_glx.so") failed: libSDL_ttf-2.0.so.0: cannot open shared object file: No such file or directory
Dumped console text to /home/zach/.ufoai/base/gl_debug.txt.
ERROR: couldn't open.
SDL audio device shut down.
recursive shutdown
Error: Couldn't initialize OpenGL renderer!
Consult gl_debug.txt for further information.


I figure that I need to download something to make this run, but don't know what to do. . .

---

### Post by Perfect Storm on 2008-05-24
Install libsdl tff, you can find it in synaptic Package Manager (libsdl-ttf2.0-0).

or
```
sudo apt-get install libsdl-ttf2.0-0
```

---

### Post by zfolwick on 2008-05-25
outstanding

---

