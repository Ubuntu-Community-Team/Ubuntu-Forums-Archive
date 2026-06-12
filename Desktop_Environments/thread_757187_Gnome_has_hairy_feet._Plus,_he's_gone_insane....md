---
title: "Gnome has hairy feet. Plus, he's gone insane..."
date: 2008-04-16
forum: Desktop Environments
---

### Post by POW R TOC H on 2008-04-16
Something's wrong with GNOME (i think). Whenever I restart my PC, applets I placed on my panels change positions and order. Even the clock, and my user name get shuffled...
What should I do? Why is this happening?

---

### Post by Druke on 2008-04-16
sounds like resolution problems, I've had that happened when applets aren't locked, but from the sound of it, you had them locked.

---

### Post by POW R TOC H on 2008-04-16
Yes, I locked them all. But, after the restarted, they're unlocked again (and moved around)...

---

### Post by Druke on 2008-04-16
well the fact that they are unlocked again says something I think, I'm not sure fo the inner working of metacity, but it sounds like the 'lock' isn't getting saved. When you restart is it a true restart or is it freezing in the restart? try logging out instead of a hard reboot.

---

### Post by POW R TOC H on 2008-04-17
It's a normal restart or shutdown... 
It doesnt happen when I restart X (with CTRL-ALT-BACKSPACE), or log out (or switch user)...

---

### Post by kirsis on 2008-04-17
Gnome's had that... shall we say, "personality quirk", since I first started messing around with Linux. So, about 4 years now ... 

It just sometimes randomly happens, then goes away. If it's persistant in your case, I suggest you file a bug or even better - go bother gnome-panel devs in some irc channel :)

---

### Post by russo.mic on 2008-04-18
Or try KDE:)

I also wanted to state, that this is the first time in almost a year on these forums I've ever used a smiley.  

A big moment for me, it was almost on instinct.

---

### Post by POW R TOC H on 2008-04-20
Congratulations on the smiley! Now, I'm a little bit new to linux (3 months or so) and I wonder : is it possible to safely install KDE, and uninstall gnome without reinstalling ubuntu, and installing Kubuntu?

---

### Post by benerivo on 2008-04-20
Yes, you can install kde and leave gnome on or uninstall it. I reccommend leaving it on whilst you try out kde. To install kde with all the kubuntu artwork, settings and kde programs, then use synaptic to install the kubuntu-desktop package. To just try out a minimal kde environment, then install kde-core.

If you install kubuntu-desktop then it will also bring in the kdm login manager and part of the installation process will ask you if you want to use kdm or gdm (the gnome one you have now). You can choose either, but i would keep gdm at this point.

If you choose to stick with kde and want rid of gnome then I think that may be a liitle trickier. I would try ```
sudo apt-get purge ubuntu-desktop
```and then ```
sudo apt-get autoremove
``` in a terminal. If you do this, then it might get rid of gdm, so then install the gdm package back on before you reboot. To get kdm on as your default, just reinstall the kdm package, and it should ask you again to pick either kdm or gdm. Pick kdm, then after a reboot you can uninstall gdm (!)

---

