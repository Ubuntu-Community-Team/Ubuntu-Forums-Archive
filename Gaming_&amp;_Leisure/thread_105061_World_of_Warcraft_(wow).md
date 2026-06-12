---
title: "World of Warcraft (wow)"
date: 2005-12-17
forum: Gaming &amp; Leisure
---

### Post by sarelphix on 2005-12-17
I installed Wine 0.93 under the 2.6.14 ck 7 vanilla kernel.  When I play World of Warcraft, everything is working.  Yet, I do not get mouse support to the degree I can't click on npcs/pc's.  I was wondering if there is a fix to this.  I have already saw this in the forums, but I spent so long searching for it and couldn't find it.  So any help or direction on where to find the answer would be helpful.

Also, I seen a multi stream how to or something on letting me use both xmms/ and another application that used sound on the board.  Can't find that either, so help on that would be greatful as well.

---

### Post by leech on 2005-12-17
For the mouse issue, you need to run 
```
export WINEPRELOADER_SETVALEGACY="no"
```
from a terminal then from the same terminal run WoW with Wine.

Leech

---

### Post by Silwenae on 2005-12-17
Is there a specific directory that has to run from?  I typed the command, and then immediately ran wine / wow from the command line, but I still can't click on NPCs.

Thanks!

---

### Post by arpunk on 2005-12-17
[https://wiki.ubuntu.com/WorldofWarcraftHowto](https://wiki.ubuntu.com/WorldofWarcraftHowto)

---

### Post by sarelphix on 2005-12-18
I tried the export bit, and that didn't work.  I uninstalled wine, and winetools, and followed the wine wiki, and i keep getting error while loading shared libraries: libwine.so.1: cannot open shared object file: No such file or directory.  So I'm not really sure whats going on, besides that while doing the install of wine from the source, didn't install the required libraries, and I don't know where ubuntu put there library files.

---

### Post by arpunk on 2005-12-18
[http://ubuntuforums.org/showthread.php?t=92367&page=4](http://ubuntuforums.org/showthread.php?t=92367&page=4)

---

### Post by sarelphix on 2005-12-18
Awesomeness, that linked helped me realize to create my own ld.so.conf file...wasn't sure if Ubuntu used it or not.  Just had to add a few missing libraries it wasn't finding.  Thanks for the help.

---

### Post by arpunk on 2005-12-18
Tell me if WoW runs for you, because i can get it running but i get missing textures and stuff, probably ATI's fault... :/

---

### Post by sarelphix on 2005-12-18
I got it running perfectly fine, but w/ the mouse pointing problem.  I have an nvidia fx5200, so that could be a problem if you have an ATI.  Try running the game w/ wine WoW.exe -opengl.  that fixed a lot of shit right off the bat.

---

### Post by arpunk on 2005-12-18
[QUOTE=sarelphix]I got it running perfectly fine, but w/ the mouse pointing problem.  I have an nvidia fx5200, so that could be a problem if you have an ATI.  Try running the game w/ wine WoW.exe -opengl.  that fixed a lot of shit right off the bat.[/QUOTE]
I can only run it with the *--opengl* option :/ otherwise it will crash. Ive found some other posts here regarding how ATI drivers sucks and games with the same problem i have (guild wars).

---

### Post by sarelphix on 2005-12-18
actually once i got wow installed the next project is to install and run guild wars...ati drivers do suck in linux...maybe you could try to copy windows ati drivers into your wine directory?  could help...not sure though.

---

### Post by arpunk on 2005-12-18
Heh, well, actually thats the perfect excuse to ask wife for a nvidia card for xmas, but sshhh, dont tell her :P

---

### Post by sarelphix on 2005-12-18
LOL awesomenes...i myself have been with nvidia since it came out w/ the geforce 2 mx, so i don't know much about ati cards besides it was never easy to install in linux.

---

### Post by glaze on 2005-12-18
Sarelphix, You have to apply a patch to Wine sources before compiling it to get mouse targeting working in WoW. It's mentioned in the Wiki, HOWTO and everywhere.

---

### Post by sarelphix on 2005-12-18
Yea I applied it to the wine source when I installed it.

---

