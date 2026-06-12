---
title: "[SOLVED] gtk-RecordMyDesktop no toolbar"
date: 2008-07-09
forum: Desktop Environments
---

### Post by jose158 on 2008-07-09
I was trying to make a video with RecordMyDesktop and then realized that I don't have a Desktop toolbar. Is there a way to stop recordmydesktop without needing the toolbar, or do I have to start it up every time I want to record something? Here is a screenshot of my desktop:

---

### Post by pytheas22 on 2008-07-09
Good for you to manage to be happy without a toolbar...I've been trying to get rid of mine in order to maximize workspace size for a long time, but even with AWN and kiba-dock, it just doesn't work for me.

Anyway, gtk-recordmydesktop is a front end to recordmydesktop, a command-line program.  If you open a terminal and type:
```

recordmydesktop
```

it will start recording.  Press control-C to stop.  Then it will build the video file and save it in the current working directory of the command prompt.

If you don't want the terminal to be visible in your screen cast, start it on another workspace.

---

### Post by jose158 on 2008-07-09
Thanks, that did it!:):guitar:

---

