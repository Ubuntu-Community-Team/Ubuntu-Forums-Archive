---
title: "Ubuntu 12.04 64bit emulator advice"
date: 2013-01-28
forum: Emulators
---

### Post by thebrandon on 2013-01-28
So I recently downgraded back from 12.10 to 12.04 and at the same time upgraded from 32 to 64 bit.  I have been trying to work out a good snes emulator but I just cant seem to find one that works as well as zsnes did on my 32 bit system so I was hoping for advice.  I tried bsnes which works the best but no matter how I change the settings it still has a bit of lag that is really annoying!  All the workarounds to get zsnes to work seemed like they were more complex than I felt was worth it.  I tried snes9x but it just crashes when I try to start it.  And finally I tried mess which insists it cant find the spc700.rom no matter where I put it or if I delete its ini file either in the /etc/mess directory or the /.mess directory.  So basically does anyone have any suggestions on how I should proceed?

---

### Post by collisionystm on 2013-01-28
> **thebrandon said:**
> So I recently downgraded back from 12.10 to 12.04 and at the same time upgraded from 32 to 64 bit.  I have been trying to work out a good snes emulator but I just cant seem to find one that works as well as zsnes did on my 32 bit system so I was hoping for advice.  I tried bsnes which works the best but no matter how I change the settings it still has a bit of lag that is really annoying!  All the workarounds to get zsnes to work seemed like they were more complex than I felt was worth it.  I tried snes9x but it just crashes when I try to start it.  And finally I tried mess which insists it cant find the spc700.rom no matter where I put it or if I delete its ini file either in the /etc/mess directory or the /.mess directory.  So basically does anyone have any suggestions on how I should proceed?


Not sure which workarounds you were using, however I installed zsnes pretty painlessly. 
I have 12.10 64bit.
I opened software sources, enabled all of them except the CD-Rom.
Opened terminal, did an apt-get update, and then apt-get install zsnes

zsnes still doesnt appear in my software center, however I have no issues installing it from the terminal.

---

### Post by ntzrmtthihu777 on 2013-01-28
A huge thanks on my part, I always ended up hunting down a .deb because it never showed up in software center (strange as I install most software from terminal with apt)

---

### Post by thebrandon on 2013-01-28
Thanks that worked great, I did have a small problem the second time I started it up it would crash but I deleted the cfg files in the .zsnes directory and now it works great.  Now I have an issue with getting it to recognize my save from my old zsnes, I put it in the .zsnes directory where I saved it from but it still starts the game from the beginning.

---

### Post by thebrandon on 2013-01-30
Well I figured out my save problem as well, it seems that before it was saving it with a space in the title but this new version was saving it without a space, I removed new file and the space in my old file and all fixed!  Thanks again for all of your help!

---

