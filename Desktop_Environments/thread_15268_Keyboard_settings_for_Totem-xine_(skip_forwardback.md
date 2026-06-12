---
title: "Keyboard settings for Totem-xine (skip forward/backwards)"
date: 2005-02-13
forum: Desktop Environments
---

### Post by stoffe on 2005-02-13
Hello, anyone know if there is any way to set keyboard shortcuts for Totem, or at least control how much it skips forward/backwards when pressing arrow right/left? I've been looking through a lot of config files and searching the net, but there seems to be no docs about this. If it is at all possible.

The really weird part is that it skips differently forward and backwards, and even semi-randomly inside those. Skipping forward mostly skips 1 minute, which often is quite long, but it seems it can be different down to about 45 seconds. Skipping backwards often skips 15 seconds the first time, and about 30 if pressing again, but again, this is not reliable, it can be anything in between. Anyone have any idea on why this is and have any suggestions for solving this? 

For keyboard skips, I like the way mplayer does it, with several options, short, middle and long skips on arrows left/right/ up/down and pageup/down. But I'd rather run Totem since it is better integrated into Ubuntu, and actually works better and on more movies right now, with the same codecs. This is with the Xine backend, of course. But in the worst case, I'd settle for being able to set the skip times, at least for now. For long skips I can use the bar, but quick key presses for small skips is just so useful, once you get used to it, and I guess I got addicted with mplayer's fine controls.

And oh, is there any homepage or list for Totem nowadays? I can't seem to find any, the one all links end up at is down.

---

### Post by piedamaro on 2005-02-13
Read the README:
H:
        Hide/Show controls in windowed mode
I:
        Switch deinterlacing on and off
P, Space (fullscreen only):
        Play/Pause
Escape (in full screen mode):
        Switch to windowed mode
F:
        Toggle full screen
0/\uffff,1,2:
        Zoom respectively to 50%, 100% and 200% of the video's original size
Left arrow:
        Go back 15 seconds
Right arrow:
        Go forward 60 seconds
Shift+Left arrow:
        Go back 5 seconds
Shift+Right arrow:
        Go forward 15 seconds
Up Arrow:
        Increase the volume by 8%
Down Arrow:
        Decrease the volume by 8%
B:
        Previous stream (Back)
N:
        Next stream (Next)
Q:
        Quit
S:
        Show the "Skip to" dialog
D:
        Toggle drawing using Gromit
E:
        Erase drawing using Gromit

Totem homepage seems down, but there is google cache for it.

---

### Post by stoffe on 2005-02-13
Thanks, I had missed that one, almost the same info is in the help file sans the part about SHIFT arrow and a few other things.

 The info about the SHIFT modifiers makes the situation a bit better, although it still skips a bit randomly.

Thanks for the info. :)

---

### Post by piedamaro on 2005-02-13
:) You're welcome, yes with some videos it can't seek properly, but usually I found no problem with big avis ;)

---

### Post by PenGun on 2008-02-11
Hey I know it's Ubuntu but try and find a command line and type "man xine".

 It will tell you more than you want to know + all the key commands for your version.

 You can do that for any command on the machine. 

 Welcome to Linux BTW.

---

### Post by Fafnr on 2008-03-01
Is there any way to modify these? I really like Totem, but I absolutely HATE these left / right arrow skips... 

/Søren

---

