---
title: "Window manager fails to start"
date: 2007-04-25
forum: Desktop Environments
---

### Post by avidesh on 2007-04-25
Window manager fails to start now after a few updates to 7.04.  It works only if I start X after booting into recovery mode. But not in usual boot.

what could be the problem and solution.

---

### Post by firfin on 2007-04-27
I think i'm experiencing the same problem.  Does this sound familiar?
After the login screen I get the standard desktop background and the taskbar in the bottom. 
Applications have no borders (so no resize , move , close, minimize etc is possible) also they don't appear in the taskbar.   Alt-tab between apps doesn't work. And also when I try the 'show desktop' button I get the following message :
Your window manager does not support the show desktop button, or you are not tunning a window manager

So apparantly something is wrong with my window manager. Does anybody know where I can find log files and stuff for the window manger so I can figure out what I need to fix?

 I am running a basically standard fiesty (upgrade from 6.10) and it worked the first times I booted

---

### Post by avidesh on 2007-04-27
yes this is exactly the same problem i face. I get the same message that you have mentioned.

---

### Post by firfin on 2007-04-27
I have found a solution that works for me. See [this topic]("http://ubuntuforums.org/showthread.php?p=2545710#post2545710") . After renaming the ~/.gnome2/session and a reboot the window manager starts fine everytime. Only thing I want now is to know what caused this. Ah well I can also hope it wont occur again :lolflag:
Anyway, I hope this tip helps you find a fix for your problem.

---

### Post by avidesh on 2007-04-27
Thanks, it worked for me too.

---

