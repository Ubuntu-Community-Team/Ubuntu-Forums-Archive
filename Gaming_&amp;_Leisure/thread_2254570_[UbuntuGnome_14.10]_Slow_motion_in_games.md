---
title: "[UbuntuGnome 14.10] Slow motion in games?"
date: 2014-11-28
forum: Gaming &amp; Leisure
---

### Post by bluesoviet on 2014-11-28
It sounds crazy, i know.  Every game that i play has this slow motion effect when something happens on the screen or when i move, however the game runs just fine if i stand still and nothing is happening. In lighter games this effect doesn't happen as often or to the degree of a game like Left 4 Dead 2, but its still noticable.  With that said, when i first installed UbuntuGnome 14.10, i had the exact same issue as posted here: [http://askubuntu.com/questions/506349/opengl-glx-context-is-not-using-direct-rendering-which-may-cause-performance-pr/538907#538907](http://askubuntu.com/questions/506349/opengl-glx-context-is-not-using-direct-rendering-which-may-cause-performance-pr/538907#538907)  However, the way in which i fixed this issue was a bit different than suggested in that topic. I can't remember all of the steps that i took, but i do remember entering the command:  sudo apt-get install fglrx    for the graphics drivers after installing Steam which replaced whatever drivers where currently installed. Perhaps this is the cause of my issue?    As some people will probably ask "How is the performance using the open-source drivers?"... well funny story about that... they don't work on my PC. I don't know why, they just don't. Switching to them results in the OS switching to the "manually" installed drivers, forcing the desktop to render in a really low resolution with huge icons. The only way to switch back(as the additional drivers window is grayed out) is by entering the command to install fglrx and rebooting.    Either way, I don't care which drivers i use... i just want to play my games without this slow motion effect. Can anyone help me achieve this?

---

### Post by mikewhatever on 2014-11-29
Can you post some specs, to start with. You seem to have an AMD graphics card wich doesn't work with many open source drivers, right? Do you know which model? If not, post the output of **lspci**.

---

### Post by bluesoviet on 2014-11-29
> **mikewhatever said:**
> Can you post some specs, to start with. You seem to have an AMD graphics card wich doesn't work with many open source drivers, right? Do you know which model? If not, post the output of **lspci**.  The Open Source drivers did work with the mainstream Ubuntu 14.04(non-Gnome) release when i had that installed(an update screwed up grub so i just installed UbuntuGnome... Gnome FTW!), that i remember.  My hardware specs: Intel I5 2320 @3GHZ (4cores) 8GB of ram AMD Radeon HD 7350.  I don't know if using the Open Source drivers will help though, last time i tried them i couldn't even get games to run at 720p at low settings(extremely low FPS, not because of the issues with fglrx). Edit: Sorry for bad formatting, Ubuntu forum messes up my text.

---

### Post by bluesoviet on 2014-11-30
> **mikewhatever said:**
> Can you post some specs, to start with. You seem to have an AMD graphics card wich doesn't work with many open source drivers, right? Do you know which model? If not, post the output of **lspci**.

oops sorry, forgot about lspci, here you go: [http://pastebin.com/uAJ2eeE5](http://pastebin.com/uAJ2eeE5)

---

### Post by mikewhatever on 2014-12-01
You might actually want to try and follow the exact steps you've linked to.  Istalling the driver is one thing, using the correct libraries - another, and both can impact performance.

---

### Post by bluesoviet on 2014-12-01
> **mikewhatever said:**
> You might actually want to try and follow the exact steps you've linked to.  Istalling the driver is one thing, using the correct libraries - another, and both can impact performance.  I don't remember what tutorial i used, just that i installed the fglrx drivers using the terminal command. Come to think of it, i think i also added an ppa too but i can't remember what the name was exactly.   So to recap on things i did:  1. installed UbuntuGnome  14.10   2. installed Steam(didn't work for same reason as link provided above)  3. added ppa from somewhere and installed the fglrx driver  4. Slow motion effect in games.   Is there a way to update everything so that its the latest build(drivers/libraries)?

---

### Post by mikewhatever on 2014-12-01
Just follow the steps and see what happens. Updating evrything is really not practical.

---

### Post by bluesoviet on 2014-12-03
> **mikewhatever said:**
> Just follow the steps and see what happens. Updating evrything is really not practical.  I did follow the steps and the result is the setup that i currently have.

---

### Post by bluesoviet on 2014-12-08
Well i tried to install my GPU drivers again to see if it would help and it bricked my install. Something about Systemmd couldn't find X.org freedesktop and couldn't start user service 1000 or something like that.  Just lovely.

---

