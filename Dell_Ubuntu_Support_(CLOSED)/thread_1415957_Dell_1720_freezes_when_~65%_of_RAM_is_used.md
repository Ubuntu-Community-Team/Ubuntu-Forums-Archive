---
title: "Dell 1720 freezes when ~65% of RAM is used"
date: 2010-02-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by muszek on 2010-02-25
Hi,

Brief description.  I have a Dell Inspiron 1720 (2GB RAM, Core 2 Duo).  Every time the RAM usage is around 1300MB (and cache takes up the rest) the machine begins to be unresponsive.  It's hard to do anything, mouse cursor stats to "hop".  It only takes a few seconds before the system becomes completely unresponsive.  Mouse doesn't move.  Sometimes I am able to switch to the console (ctrl+alt+f1) - sometimes I can't even log in there - after typing in my username it doesn't display the "enter password" line and then I get the "60 secs timeout".  
Most of the time (not always) I can hear the hdd doing something.  If I wait long enough (a few minutes - few tens of minutes) it becomes responsive again (but I need to close something first or else I'm in trouble again).  Today after 20 minutes of waiting (still unresponsive) I went out.  2 hours later it was responsive.
AFAIR the "raising skinny elephants" combo always works.

Additional information:
 * I can't recall exactly when it started to happen.  Last few months probably.  Big changes in that time frame - installed Karmic (from scratch) and it's the first time I'm using a 64-bit distro.  Switched from Firefox to Google Chrome as my main browser (it eats a lot of memory).
 * been using this laptop since Feisty (7.04) and I don't think I've had this problem before.
 * I tried to play around with swappines param and turing of swap completely.  It probably freezes more often when the swap is off, but when it's on, it's driving me nuts, cause "using" the swap slows down the machine considerably (lappy hard drive ain't too fast).
 * stuff I have opened at all times: google chrome, geany, guake, gnome-terminal, rhythmbox and/or banshee, dropbox, nautilus and everything that gnome loads by default.
 * I get it a few times a day.
 * It is a major PITA - I have to reboot the machine via "raising skinny elephants" (this can't be healthy) a few times a day and are caught off-guard (although I save my work really often).

Please help me diagnose and get rid of this problem.

---

### Post by mörgæs on 2010-02-25
How does the machine behave with a 32 bit 9.04 live CD? 

Have you tried running memtest?

---

### Post by lemmyg on 2010-03-19
Hi, 
I have Dell Inspiron 1720 with karmic. I haven`t any freezes issue. all works well, except mic volume record. Record sound very low. I have swap value to 60. Anyway I think your memory consumption is excessive. 
You can look with "top" process memory consumption. 

uname -a
Linux 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010 x86_64 GNU/Linux

---

