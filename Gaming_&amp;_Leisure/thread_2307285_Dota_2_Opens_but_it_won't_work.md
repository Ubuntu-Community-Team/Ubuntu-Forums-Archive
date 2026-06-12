---
title: "Dota 2 Opens but it won't work"
date: 2015-12-23
forum: Gaming &amp; Leisure
---

### Post by baris6 on 2015-12-23
Greeting everyone,here is this thing:I am new to Ubuntu, I downloaded steam and dota yesterday. Today, I tried to play dota but the same thing keeps on occuring ; I open it, I am seen :In- Game , when I try to click again I get the message "Dota 2 is already running" but I can't find the window or the game or tab or anything related to it. And the worse is I can't even close Steam because I can't close dota at all. I tried many solutions that I've seen on these forums, none of them worked and I had to reboot my computer everytime I wanted to try a new thing ; that was because I was unable to exit Steam. Any help is appreciated, thank you.

---

### Post by oldrocker99 on 2015-12-23
Try this:```
sudo apt-get install htop
htop
```

This will start a process manager. Hit F3 and type in (without quotes) dota, and if that returns nothing, DOTA. Then hit F9 to kill it, and choose SIGKILL and DOTA will be gone.

Or, the System Monitor can do the same thing, with a right-click on the DOTA line. I just like htop;).

---

