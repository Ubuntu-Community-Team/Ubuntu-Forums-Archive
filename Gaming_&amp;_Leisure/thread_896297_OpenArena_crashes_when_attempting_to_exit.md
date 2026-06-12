---
title: "OpenArena crashes when attempting to exit"
date: 2008-08-21
forum: Gaming &amp; Leisure
---

### Post by George_ on 2008-08-21
OpenArena is fine while I'm playing, but when I click 'Exit' and the screen comes up saying 'Click or press any button to exit,' whenever I click or press a keyboard button the whole thing freezes, and the mouse and keyboard become unresponsive, I have to restart my computer to get rid of the crash. This problem has just arisen after I updated to 0.7.7, is anyone else having this problem? And how do I fix this?

Thanks

---

### Post by cristo-father on 2008-08-21
Try the newest version.
[http://www.getdeb.net/app/OpenArena](http://www.getdeb.net/app/OpenArena)

---

### Post by George_ on 2008-08-22
No, the problem's still there, even with the new version. Again, the game itself works perfectly fine, but becomes unresponsive when I try to quit.

---

### Post by klosterdev on 2009-01-07
Mine crapped out midway through the game, resized itself to a window on my desktop, and froze everything.  Had to restart.

---

### Post by gamgee911 on 2009-06-09
Having the same issue here, using latest version.  Anyone get a fix for this yet?

---

### Post by tehweezil on 2009-12-19
Same issue with Karmic 64x, it works fine during the game but crashes on exit. It didn't do this with the previous version of OA for me, just on 8.1-4

---

### Post by tehweezil on 2009-12-19
> **klosterdev said:**
> Mine crapped out midway through the game, resized itself to a window on my desktop, and froze everything.  Had to restart.

Hmm, try playing it with fullscreen disabled, because I used to have the same issue. Every time a notification would appear the game would freeze and leave fullscreen. You might be having a different problem but disabling fullscreen helped me :)

---

### Post by MrNatewood on 2010-03-20
Same problem in Karmic 64. Anyone found a fix for it?

---

### Post by cgroza on 2010-03-20
to avoid restarting the pc every time crashes press ctrl+alt+f1 and killall openarena

---

### Post by Eonfge on 2010-04-05
I found the same bug, but only more extended. At first I thought it was about [a bug in libsdl1.2]("https://bugs.launchpad.net/ubuntu/+source/libsdl1.2/+bug/162151") but this crash happens on exit of multiple full screen games. 

TeeWorld and Enemy Territory both crashed the system (and now with your advice, i can restore it) to a frozen state. It did not happen to Urban Terror when I tested it, and also Enemy Territory suddenly works fine at the first exit, but now it snaps when I try to load a mod and it has faff about for a minute to continue process. Exiting on the other hand all worked on my second test round. TeeWorld didn't. It scared shitless when I turned Full screen back on and died the moment I hit "yes" to exit.

I tested this on a HP pavillion DV6 Laptop with a Ati mobile video card and a intel processor (8 months old).

Could someone help me out if I somehow did something wrong my self. I'm student and although I fully support linux and it's ideas, I'm relatively new to the system it self. It might be that I did something wrong my self, please tell me then.

---

### Post by NightCrawler03X on 2011-11-29
I came to this thread after searching google for a solution to the same problem. I'm using Debian Squeeze/Stable (AMD64 version), but I still have

One word of caution:
killall openarena,
this still leaves a zombie process running. If you run openarena from your xterm maybe you would recieve some useful output to say why it crashes.

Sapphire HD 5670 using AMD binary drivers. I have not tested with open source ones.

```

----- CL_Shutdown -----
Received signal 15, exiting...
----- CL_Shutdown -----
WARNING: Recursive shutdown

```

I'm guessing that those dead zombie processes are doing something weird.

On further inspection, the zombie processes disappear.


I did not get this error ever on Xubuntu, and never on debian until nev. It seems intermittent. If it happens to everyone here (on different cards and drivers I assume), then its not my setup.

Its a bug in OA.

But, Ubuntu and Debian probably include an older version. Try purging it with apt-get and installing the latest version manually.

---

### Post by NightCrawler03X on 2011-11-29
solution:
its a hackish one, but it works.

When ekiting the game, DONT EXIT.

Come out of fullscreen, press tilde to get the quake console, you will have mouse control.

Close the window with the X in your window manager.

This didnt actually close it for me, but then I could Ctrl-C from the terminal that I ran OA from, and run
killall openarena,
from the console.

It beats having to ctrl-alt-f1.

---

