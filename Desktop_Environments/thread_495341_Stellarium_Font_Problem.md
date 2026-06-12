---
title: "Stellarium Font Problem"
date: 2007-07-07
forum: Desktop Environments
---

### Post by SteinbergerNate on 2007-07-07
I just installed Stellarium and when I run it all the fonts show up as dashes. I'm running with just standard US English. Anyone with similar problems know how to fix it?

---

### Post by Gwasanaethau on 2007-07-21
I'm also having the same problem. It worked correctly in Edgy…

---

### Post by crimesaucer on 2007-07-21
Works fine in Feisty for me. (I love this stellarium)

---

### Post by SteinbergerNate on 2007-08-15
Ok, update on my problem. I've gotten the open source ati driver to work properly on my computer and I'm getting direct rendering. I read somewhere that if you don't have openGL working properly then it causes problems with stellarium fonts.

My question is if anyone else has had problems with the fonts in stellarium using the open source ATI driver instead of the closed binary driver. If so, what did you do to get it working properly?

---

### Post by wrongo on 2007-08-21
> **SteinbergerNate said:**
> Ok, update on my problem. I've gotten the open source ati driver to work properly on my computer and I'm getting direct rendering. I read somewhere that if you don't have openGL working properly then it causes problems with stellarium fonts.

My question is if anyone else has had problems with the fonts in stellarium using the open source ATI driver instead of the closed binary driver. If so, what did you do to get it working properly?

Wait. How did you get the open source ati driver to work properly on your computer, please?

Or, re: your question, I'm having problems with fonts in stellarium, but I don't KNOW if I'm using the open source ATI driver or the closed binary driver. I don't even know what those are. How do I determine which one I'm using?

---

### Post by tukuyomi on 2007-08-22
Hi, I've the same font problem as SteinbergerNate and I'm using ati/radeon libre driver (didn't test with fglrx as my graphic card isn't supported anymore...)
> **wrongo said:**
> Or, re: your question, I'm having problems with fonts in stellarium, but I don't KNOW if I'm using the open source ATI driver or the closed binary driver. I don't even know what those are. How do I determine which one I'm using?
Something like ```
$ cat /etc/X11/xorg.conf | grep Driver
        Driver          "kbd"
        Driver          "mouse"
        Driver          "ati"

``` can answer your question.
- If it tells you "ati" or "radeon", you're using the libre ati driver.
- If It tells you "fglrx", you're using closed ATi driver
- if it tells you "vesa", you can't have Direct rendering. Edit your xorg to replace "vesa" with "ati".
```
$ glxinfo | grep rendering
direct rendering: Yes
``` tells you about Direct rendering.
--
I found another similar font glitch, not with stellarium, but when you stop gdm from a tty:
```
CTRL+ALT+F1 and then
$ sudo /etc/init.d/gdm stop
```
There, I can't read anything on my console, the fonts are quite similar as in Stellarium. To come back to gdm, if you can't read anything, press UP once (command history: sudo /etc/init.d/gdm stop) then BACKSPACE twice (delete "op" from "stop") ans hit "art" (replace "stop" with "start")

---

### Post by Gwasanaethau on 2007-08-26
Ooops! 8-[ I forgot to look back here again, but if it's any help to yez I managed to fix it - by replacing my graphics card! Expensive and overblown, I know, but I needed a new one for various other reasons. It seems to have fixed it.

Oh, and by the way, I was using the fglrx ATi drivers on my Radeon 9250. I now have an nVidia…

---

### Post by SteinbergerNate on 2007-08-27
Yeah, I had a feeling it had something to do with ATI. Unfortunately, that option is out of the question since I'm on a laptop (unless my wife lets me remove XP from the desktop for Ubuntu. It already has a Nvidia card in it.)

Edit: and to further answer the earlier question of how to get the open driver working, you make sure that there is no fglrx packages on your installation (these will override the open driver every time) and change the driver in your device section of xorg.conf to ati.

---

### Post by wrongo on 2007-09-23
> **SteinbergerNate said:**
> Yeah, I had a feeling it had something to do with ATI. Unfortunately, that option is out of the question since I'm on a laptop (unless my wife lets me remove XP from the desktop for Ubuntu. It already has a Nvidia card in it.)

Edit: and to further answer the earlier question of how to get the open driver working, you make sure that there is no fglrx packages on your installation (these will override the open driver every time) and change the driver in your device section of xorg.conf to ati.

OK. How do I "make sure there is no fglrx packages" on my installation? (Sorry, I just don't know!) I'm "ati" and "yes" on the first two commands a few posts back. I'm still having font problems. How do I fix the "fglrx" packages if I need to? Thanks!

---

### Post by tukuyomi on 2007-09-24
It doesn't have to do with fglrx as I'm not using it...
Anyway, removing fglrx requires [those steps (https://help.ubuntu.com/community/RadeonDriver#head-229f59879c2a2b6c6635d1e189706d97f836b879)]("https://help.ubuntu.com/community/RadeonDriver#head-229f59879c2a2b6c6635d1e189706d97f836b879"), I add this one for the sake of it:
- fglrx is not written in /etc/modules; something like ```
$ cat /etc/modules | grep fglrx
``` should return nothing; else, ```
$ sudo nano /etc/modules
``` to actually remove the line 'fglrx'
Here you go =)

---

