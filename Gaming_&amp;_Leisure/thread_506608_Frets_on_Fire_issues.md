---
title: "Frets on Fire issues"
date: 2007-07-21
forum: Gaming &amp; Leisure
---

### Post by rustysail on 2007-07-21
```
Traceback (most recent call last):
  File "./FretsOnFire.py", line 64, in <module>
    engine = GameEngine(config)
  File "/usr/share/games/fretsonfire/game/GameEngine.py", line 155, in __init__
    self.video.setMode((width, height), fullscreen = fullscreen, multisamples = multisamples)
  File "/usr/share/games/fretsonfire/game/Video.py", line 68, in setMode
    self.screen = pygame.display.set_mode(resolution, flags)
pygame.error: Couldn't find matching GLX visual
```

I can't figure out what to do.  I tried installing in a .deb and downloading it form their site, but it won't work.

Thanks for the help.

---

### Post by slimdog360 on 2007-07-22
You don't really need a deb file. what is that output from? did you try running the .py file from their download on their main site?

---

### Post by rustysail on 2007-07-22
That output is from trying to run ./FretsOnFire from the download on their site.  I tried a deb from the ubuntu site and after installing I got the same error message.

I'm not sure which .py file , but I'll try to find it.

edit: I can not find any .py files.  There are files that begin with pygame. though.

---

### Post by rustysail on 2007-07-22
Hey I still haven't made any progress.  The problem is with GLX visual, but I'm not really sure what that is.

Could use some help.
Thanks

---

### Post by Dpdk on 2007-12-02
if its asking for glx then you need to make sure that you are using the right driver for your video card ie the nvidia driver instead of nv for NVIDIA cards.

---

### Post by go_beep_yourself on 2007-12-09
I'm having the same problem, and I am using nvidia, not nv. Did you download Frets on Fire from getdeb.net?

---

