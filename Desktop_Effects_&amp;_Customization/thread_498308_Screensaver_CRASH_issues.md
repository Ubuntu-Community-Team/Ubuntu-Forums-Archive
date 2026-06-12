---
title: "Screensaver CRASH issues"
date: 2007-07-11
forum: Desktop Effects &amp; Customization
---

### Post by Beatbreaker on 2007-07-11
hey i'm not sure what's happening with this one (also not sure if compiz-fusion is causing it) but say if my screensaver goes on for a little while, maybe any time over an hour - MOST of the time it will get stuck and sorta crash i don't know why.

say if i've left the computer on screensaver for ages - then move the mouse - i can see the mouse pointer, but i don't get returned to my desktop (or i don't get prompted to enter in my password to be returned to my desktop more accurately)  - i can seem my mouse and control it, but clicking on things dosen't do anything.... and also if i press CTRL + ALT + BACKSPACE i can be taken back to the log in screen. i just don't understand what's going on, somehting must be crashing?

is it fusion? is it my screen off power management settings? is it my screensaver? - any idea? i wouldn't even know where to find the log file to checkout what's going wrong here.

any help is most appreciated.

---

### Post by ikariotis on 2007-07-11
Greetings, 

Before I begin let me say my Ubuntu experience has been pretty good. This is my first post on the forums....

Anyway, I just wanted to say that I have the exact same problem as the previous post. Is there anyway we can fix this problem or disable Compiz for certain applications? That would be really helpful.

Thanks :KS

---

### Post by ikariotis on 2007-07-12
Greetings everyone,

I don't know if anyone even see this thread but I have found that not all screen savers make the computer crash when Compiz Fusion is running. I went through all the screen savers and found that it is these that cause the problem (at least on my computer). I removed the following screen savers and it seems to be ok now. Hope this helps. 

braid
whirlwindwarp
glblur
gleidescope
glforestfire
glhanoi
glknots
glmatrix
glplanet
glslideshow
glsnake
gltext
interaggregate
nerverot

---

### Post by ztirffritz on 2007-08-21
I've found that many more screen-savers than what you have listed cause X to crash.  I've gone with a blank screen and it seems to work though.  I'm using Compiz-Fusion with indirect rendering (compiz --replace --indirect-rendering) to launch Compiz because I get the "black screen' error otherwise.

---

### Post by war59312 on 2008-01-12
Yeah wish I saw this post, screen saver is stuck on interaggregate and cant change it to something else since it freezes every time I open screensavers.

Have to force a reboot via alt+sysrq+b. ok n/m switch visual effects to none and no issue.. would be nice if this was fixed already..

---

### Post by xjgnsdof on 2008-01-26
Same problem with the "interaggregate" screensaver (possibly others)... I'm probably going to just delete it and the others specified in this post.

---

### Post by glennric on 2008-02-01
Do all of you that have this problem have nvidia video cards?  I have this problem on a computer that has an nvidia card, but not on any other computers.  I have also noticed that some screensavers work with xscreensaver but not with gnome-screensaver and vice-versa.  Of course when metacity is running instead of compiz they all work.

---

### Post by MikeCheck on 2008-02-07
For me, I think it is just the Braid screensaver that is causing problems.
I do have an Nvidia graphics card.
When you say that you deleted the screensavers, do you just delete them from /usr/lib/xscreensaver?  Is there anything else that has to be done?

---

### Post by FuturePilot on 2008-02-07
I have this issue too. There's a bug report here
[https://bugs.launchpad.net/bugs/101943]("https://bugs.launchpad.net/bugs/101943")

---

### Post by ktulu1115 on 2008-03-08
Same issue with me here.  Using GLscreensaver, but havn't tried others yet.  Using NVIDIA card here.  I've found a hack that sorta works sometimes - switch to a virtual terminal (Ctrl-Alt-F1), then back to X (F7).  Most (not all) of the time, the screen comes back OK for me.

---

### Post by bazaloo on 2008-04-26
Im running Ubuntu 8.04. This is what I did

[LIST]
[*]cd /usr/lib
[*]sudo mv xscreensaver xscreensaver.bak
[/LIST]

Then open System > Preferences > Screensaver and choose Blank Screen or another screen saver that doesn't crash. Then go back to the command line and rename the screensaver folder back to what it was.

[LIST]
[*]sudo mv xscreensaver.bak xscreensaver
[/LIST]

---

### Post by bengoza on 2008-05-28
I also have this issue, mostly with Braid and Interaggregate. Only when they freeze my screen I can't even Ctrl+F1, or anything. And yes, I have an Nvidia graphics card. How do you uninstall specific screensavers?

Answered my own question: ```
sudo rm -f /usr/lib/xscreensaver/interaggregate
```
replace the interaggregate part with any screensavers that are giving you trouble.

---

