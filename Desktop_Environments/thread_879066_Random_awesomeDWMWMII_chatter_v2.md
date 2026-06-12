---
title: "Random awesome/DWM/WMII chatter v2"
date: 2008-08-03
forum: Desktop Environments
---

### Post by shearn89 on 2008-08-03
Since the old thread got locked with the forum update, here's the new v2.
Mods - if anyone feels this is in the wrong forum, please move it. The last one was in this subforum, and was a general support thread for all tiling wms, so i guessed the new one could be too...

Let me start out by saying that i just finished submitting my new howto:

[SIZE="5"]"Howto: Write an awesome 3 rc file".[/SIZE] At least, i think that was the title. If/when it gets approved, i'll post a link. When awesome 3 is finally released (rc came out quite recently), i'll redo my old "installing awesome" one.

---

### Post by jetsabel on 2008-08-15
i'm looking foward to this howto!

---

### Post by Sammm_ on 2008-08-18
I'm desperatley trying to compile dwm to replace awesome (it keeps making my pc crash, odd). Anyway I'm getting this error when compiling, and I can't find out how to resolve it...

```
dwm build options:
CFLAGS   = -std=c99 -pedantic -Wall -Os -I. -I/usr/include -I/usr/X11R6/include -DVERSION="5.1" -DXINERAMA
LDFLAGS  = -s -L/usr/lib -lc -L/usr/X11R6/lib -lX11 -L/usr/X11R6/lib -lXinerama
CC       = cc
CC -o dwm
/usr/bin/ld: cannot find -lXinerama
collect2: ld returned 1 exit status
make: *** [dwm] Error 1

```

Anyone have any idea how to resolve it?

**Solved - I should of read all the files first, I just commented that part of config.mk out.**

---

### Post by mali2297 on 2008-12-14
I have just now installed awesome 3 (the latest 3.1). I am trying to figure out how to adjust the window placement so that the windows won't overlap in floating mode. 

I can set *awful.placement.no_offscreen* and *awful.placement.no_overlap* inside *awful.hooks.manage.register*. That solves the problem when I open new windows in floating mode. However, when I open windows in tiling mode and then switch to floating mode, the windows get stacked on top of each other in the upper left corner. Does anyone know a solution?

---

### Post by shearn89 on 2008-12-14
completely forgot about this thread - I guess my howto never got accepted. Maybe i'll just update the old one...

anyway - not sure how to get around this. I'd guess you could code something into one of the hooks similar to what you've already done? I'm not that good with lua though, so I can't help too much...

---

### Post by mali2297 on 2008-12-14
> **shearn89 said:**
> completely forgot about this thread - I guess my howto never got accepted. Maybe i'll just update the old one...


Isn't it [here](http://ubuntuforums.org/showthread.php?t=879059)?

---

### Post by shearn89 on 2008-12-14
aha! thanks a lot... update coming after some revision has been done (exams next week).

---

### Post by dbbolton on 2009-03-07
Maybe one of you guys can help me out. I'm having trouble with certain windows showing up beyond the edge of the screen. I started a thread about it here: [http://ubuntuforums.org/showthread.php?t=1089832](http://ubuntuforums.org/showthread.php?t=1089832)

---

### Post by zedwards on 2009-04-12
Artwiz...The last thing I want to perfect my wm. I cannot for the life of me get artwiz fonts to show in wmii. I have done everything but they just don't show up as installed in xfontsel but they do show up in my font catalogue. Any ideas?

---

