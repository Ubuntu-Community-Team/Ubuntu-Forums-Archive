---
title: "pcsx (from software center) not working"
date: 2015-03-24
forum: Emulators
---

### Post by lou6 on 2015-03-24
I installed pcsx from software center on Trusty. Menus of several games (Tomb Raider, Tomb Raider II, PGA Tour) look fine but games will not run - they go to black screen.

I've tried installing libstdc++5 (per another post) with no joy.

Can someone help me?

---

### Post by dino99 on 2015-03-24
that software was updated for the last time on 15-jun-2012 ; so it looks like abandonware
maybe you got some usefull warnings/errors logged to help narrowing down that issue.
what is the terminal output when you run it ?

---

### Post by lou6 on 2015-03-24
No output at all when run from terminal...

---

### Post by deadflowr on 2015-03-24
Moved to Gaming >> Emulators

You need a bios file.
pcsx comes with a generic bios file(it's a simulated bios file), but does not work with a lot of games, from what I've been able to tell.

---

### Post by lou6 on 2015-03-24
I've tried bios SCPH1001.BIN with no success. Do you have a better suggestion?

---

### Post by deadflowr on 2015-03-24
Which graphics are you using xvideo driver or opengl driver?

---

### Post by lou6 on 2015-03-24
opengl

---

### Post by deadflowr on 2015-03-24
If you move your mouse over the Ubuntu top panel, while pcsx is open, the menu should show.
In the menu item configuration go to plugins and bios.
In plugins and bios can you change the selection from the opengl setting to the xvideo setting?
If so, and you run a program, does it change any of the previous problems?

---

### Post by lou6 on 2015-03-24
plugins and bios is greyed out while pcsx is running a rom.

I also tried xvideo from the start but that gets an immediate black screen - no video at all when running a rom.

---

### Post by lou6 on 2015-03-25
Well, I guess I'll add pcsx to the list of apps in the software center that don't work.

Thanks to those who replied and tried to help...

---

### Post by lou6 on 2015-03-28
After some research I found that the games I was trying both contained cdda audio tracks and pcsx does NOT like cdda audio. 

Games that do not use this audio format play fine.

---

### Post by michael-piziak on 2015-06-28
It should work.  Perhaps it's your particular computer.  I'm running PCSX on my sisters 14.04 lts system and on my 12.04 lts system.
Granted, only about 60% of the roms will work.  But that is consistent on both systems and just they way it is.  Unlike other emulators, like the snes emulators, which run 99% of their roms.

You might try downloading some more roms and seeing if you can get them to work.  That's my only thought right now.  Other than making sure FPS limit is turned on.

p.s. I just seen your latest post where you can get some games to work.

---

### Post by GeorgeLSpencer on 2015-10-09
There are later versions of PCSX than the one available from the software centre. Try these and, if you are lucky, they will work for you. I am using iso files, and find that the emulator is pretty good with these.

---

### Post by General_Faliure on 2015-10-16
The original pcsx is dead, here is a new one: [URL="http://www.epsxe.com/"]http://www.epsxe.com/
[/URL]

---

