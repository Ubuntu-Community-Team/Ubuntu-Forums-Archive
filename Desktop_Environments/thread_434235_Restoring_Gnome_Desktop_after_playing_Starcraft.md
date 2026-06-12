---
title: "Restoring Gnome Desktop after playing Starcraft"
date: 2007-05-05
forum: Desktop Environments
---

### Post by tonester on 2007-05-05
I am running gnome under edgy and my desktop spans across dual monitors. The resolution for each monitor is set at 1280x1024.

I wrote a simple shell script that does the following:

mounts an .iso of starcraft broodwar
runs the program through wine
when I exit the game, unmounts the .iso

The game runs at a resolution of 800x600 (fullscreen) on one monitor while the other monitor is in sleep mode. 

The problem is that at the conclusion of the script (game), all of my icons and panels are bunched into one monitor at the lower resolution, and I have to reset gnome manually to get it back to where it was (along with manually moving the icons and panels back, etc).

Are there any commands that can store the original state of the desktop and restore it back automatically at the end of the script so I don't have to do the <CTRL><ALT><BACKSPACE> business?

Thanks in advance...

---

### Post by Leszek Tarkowski on 2007-05-06
I suggest you to start starcraft in another X session. There are bunch of hotwos, especially if you are using beryl/compiz. 
Simplest one is:

```
startx your_script.sh -- :1 -depth 24
```

and you can shift between sessions using alt-ctrl-F7 alt-ctrl-F8

---

### Post by tonester on 2007-05-06
Thanks - I'll try that out!

---

