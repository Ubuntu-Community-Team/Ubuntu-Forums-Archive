---
title: "Severe Issues on Game Exit"
date: 2007-08-29
forum: Gaming &amp; Leisure
---

### Post by graceofdragons on 2007-08-29
I just got back into Linux this morning with the latest Kubuntu, so far everything has been flawlessly good. 

I got WoW to work after about an hour, with wine and running OpenGL configs and RegEdit tweaks. Works perfect save I'm forced to Run it in Windowed Mode and Maximized. (Because the Taskbar and Application bar were showing up over the game) This also removes my ability to alt-tab. But it does work flawlessly at 50+ FPS with Max Settings.

Here comes the real issue. Upon /quit from WoW the OSS Sound continues to run, It's clearly at the login screen, the window is still active however the graphics are turned off. It doesn't even slow the rest of my system down, just sits there and makes noise, and I can not Kill it. 

Reboot has been my only option. I'm 100% sure this is due to my linux noob status.

I'm at work now, and I just read another thread on opening in it's own X window, I'm going to try that when I get home. Is there anything else I should be aware of?

---

### Post by disturbedite on 2007-08-29
well, wish i could be of more help, but the only info i have to offer is that i've had this same problem with one game before with wine.  (i forget exactly which one, it might have been d2).  i haven't experienced it since, but rebooting was the only thing that "solved" it.

so at least you know it has happened before to someone else...

---

### Post by uberbitter on 2007-08-29
I have been having a similar problem.  Two versions of wine ago I was able to cleanly exit from World of Warcraft most of the time, but as of one version ago it crashed sometimes, and with the current release (0.9.44) it crashes every time.  

I've been running the game in a new X session (to get around the fact that not doing so means I cannot type in the username and password fields and that the game will run the sound on startup but not the graphics), but that doesn't help the crashing on exit.

---

### Post by graceofdragons on 2007-08-29
I got some ideas, I'll work on them in the morning, and see if I can get any progress. I'll let you know.

---

### Post by cogadh on 2007-08-30
Have you tried running "wineserver -k" in the terminal? That will usually kill any running Wine app, even when you can't kill that actual running .exe file.

---

### Post by disturbedite on 2007-08-30
forgive my ignorance, as i've never done it before, but how would i go about running x in a new session?

---

### Post by cogadh on 2007-08-30
Click on the "Stuff I've learned about Wine" link in my sig and go to the "Advanced stuff" section, it is explained in detail there.

---

### Post by disturbedite on 2007-08-30
cool.  thanks cogadh.

---

### Post by Pikestaff on 2007-09-01
A similar problem was happening a few wine updates ago, somebody posted a script that offers a sort of temporary fix... (or at least a way to close it when it freezes up):

Alt+Tab out of WoW to a terminal and paste this in:

```
#!/bin/bash

for i in $(pidof WoW.exe); do
    kill -9 $i && sleep 1
done
```

And that should fix it for you!  I can't remember who first wrote up this little script but it has always worked for me when WoW freezes on exit (or any other time.)

As for a permanent fix to this problem, I believe this is one of those things where you sort of have to wait it out because I think it's either a Blizzard thing or a WINE thing but I could be wrong.

---

### Post by Ardrias on 2007-09-01
It's some incompatability of sorts with new stuff in Wine 0.9.44 (cant remember/be bother to find link) but just log out of your char first, so settings are saved and then do 'wineserver -k' in a terminal :)

---

