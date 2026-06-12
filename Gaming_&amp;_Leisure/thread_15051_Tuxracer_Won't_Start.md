---
title: "Tuxracer Won't Start"
date: 2005-02-11
forum: Gaming &amp; Leisure
---

### Post by Sapper2ID on 2005-02-11
Last time I installed with synaptic, I could launch from apps/games, it's not there. I did /usr/games/tuxracer and got this  

"open /dev/sequencer: No such file or directory
Fatal signal: Segmentation Fault (SDL Parachute Deployed)"

It tries to start(blackscreen) then CTD. Do I need something from synaptic?
Is the tiny tnt the problem? 6111 drivers are in.  Enemy Territory does the same but I have a launcher in apps/games.

"couldn't exec language.cfg"
"couldn't exec autoexec.cfg"

"Sys_LoadDll(/root/.etwolf/etmain/ui.mp.i386.so) failed:
"/root/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok"  It says that 2X
I put in "et" in root console, Most of the info is good, say's card is good, sound, etc. Sorry to put 2 problems together but I was already here. Thanks.


Warty-K7
800mgz Athlon T-Bird
K7T Pro
128mg/pc100
RIVA TNT2 16mb
2 HDDs 100ggs
AC97

---

### Post by jdodson on 2005-02-11
try killing the esd proccess for tuxracer.

try this for enemy territory: [http://ubuntuforums.org/showthread.php?t=10594](http://ubuntuforums.org/showthread.php?t=10594)

---

### Post by Sapper2ID on 2005-02-11
Killed esd in system monitor, no joy
Installed supertux to see if it would work, no problems. Starts right up.

---

### Post by Sapper2ID on 2005-02-12
ET still not working after following above thread. I'm going to let it rest for a day and try things again

I D/L'd and installed the Wolfenstein SP demo for linux (full). Installed without a hitch. 
I can start and get all the way to chose difficulty, click, crash. The only error in all the text is at the very last it says "Received Signal 11- Exiting". Sooo close!

---

