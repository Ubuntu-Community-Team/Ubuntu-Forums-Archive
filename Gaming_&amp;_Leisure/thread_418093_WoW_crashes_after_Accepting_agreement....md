---
title: "WoW crashes after Accepting agreement..."
date: 2007-04-22
forum: Gaming &amp; Leisure
---

### Post by donoman on 2007-04-22
OK I dont know much about computers but I got my bro to set up WoW on this comp for Linux. So yeah it worked on the last version of Ubuntu but now we've upgraded and I got a big problem :O.

This is what I did, after my bro set up wine and everything. I install WoW TBC and the menu/character screen worked fine, I was in direct 3d btw (with no performance optimization on yet)  so that I could edit my video settings. Anyway I log into the game and it loads for ages and then I get in. So after a few things load, some NPCs and the enviroment the computer absolutely freezes, and I had to reset. My second attempt I tried going on -opengl, I load up the game and the user agreement thing pops up, the graphics are decent in the background, less choppy then direct 3d... anyways after I click down both agreements the computer freezes. I try again in direct 3d again and the same thing happens. I reinstalled WoW and Wine and still get this bug. PLEASE does anyone know why this is happening... Linux can be very frustrating some times.

BTW...

ATI Radeon 9600 SE
something like 500 SE ram
1.8 ghz processor
... dunno much, but when windows was still on this comp I usually got 30 frames in wow.

---

### Post by lakersforce on 2007-04-22
Perhaps you experience something simillar to what I desribed here?

[http://ubuntuforums.org/showthread.php?t=413766](http://ubuntuforums.org/showthread.php?t=413766)

---

### Post by donoman on 2007-04-22
Yes the music was playing when the game had crashed. But you say you could go back to desktop, : /, and also you arnt getting the problem where the game crashes after the 2nd terms of use agreement.

---

### Post by lakersforce on 2007-04-22
No, I have already accepted the license agreement, so I have never tried that. You can kill the process. Place a terminal in your upper bar. When the game crashes press ctrl+alt+esc. This brings up the desktop (on Gnome). Open a terminal and type:

```
sudo killall WoW.exe
```

You might have to do it a couple of times, before it actually closes.

---

### Post by donoman on 2007-04-22
every time i log in hiave to do a use agreement -_-... ty for that it might help, but if ne1s got real fix, appreciate it.

---

### Post by lakersforce on 2007-04-22
You might want to try adding the following lines to your config.wtf:

```
SET readTOS "1"
SET readEULA "1"
```

---

### Post by donoman on 2007-04-22
their alrdy there, typing with 1 hand, apologise for grammar :(

---

### Post by donoman on 2007-04-22
Bump?

---

