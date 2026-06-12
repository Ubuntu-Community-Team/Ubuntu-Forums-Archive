---
title: "Only One Instance of MPlayer Please?"
date: 2006-02-16
forum: Desktop Environments
---

### Post by kimvall on 2006-02-16
Is it possible to control how many instances of MPlayer that can be created? When I open a video file, I want it to start MPlayer and then play the file.

If MPlayer is already running, then I want the file to be played in that MPlayer instance, and not create a second one.

Is this at all possible?

---

### Post by BluParadox on 2006-03-10
I've got this same problem. I've been looking everywhere and cannot seem to find a solution (I found some cool other things though, lol)

---

### Post by srg84 on 2007-08-18
Make a file called MPlayer1.sh:
[B]
gedit  MPlayer1.sh[/B]

paste this:
[B]
killall -9 mplayer
/usr/bin/mplayer -gui -p "$1" 
 [/B]

Execute permissions:
[B]
sudo chmod +x  MPlayer1.sh[/B]

Open All video files with MPlayer1.sh:

**"Open With" In Nautilus, personalized command.. , and browse to  MPlayer1.sh. It should be in /home/USER, but the location doesn't mind**

Done :D.

PD: If you change something in configuration, you must close mplayer to grab the settings, because the command "killall -9 mplayer" kills the process before the settings are stored

---

### Post by six^letters^digits on 2008-05-06
> **srg84 said:**
> 
Make a file called 
MPlayer1.sh:
[B]
gedit  MPlayer1.sh[/B]

paste this:
[B]
killall -9 mplayer
/usr/bin/mplayer -gui -p "$1" 
 [/B]


> **srg84 said:**
> 
PD: If you change something in configuration, 
you must close mplayer to grab the settings, 
because the command 
"killall -9 mplayer" 
kills the process before the settings are stored


why kill before invoking ?

where is a description of mplayer's
    -gui  and  -p  options ?

---

