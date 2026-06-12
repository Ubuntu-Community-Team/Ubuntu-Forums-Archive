---
title: "configuring extra mouse buttons"
date: 2009-09-23
forum: Desktop Environments
---

### Post by geoffm on 2009-09-23
I have 2 buttons on the side of my mouse. I use them to switch to desktop left/right. I could easily configure that with compiz, but I disabled compiz because I started prefering speed over eye candy (have a shitty graphics card)

But there's no easy way in gnome to configure those buttons. I read the wiki
[https://help.ubuntu.com/community/ManyButtonsMouseHowto](https://help.ubuntu.com/community/ManyButtonsMouseHowto)
but it doesn't help because it only says to install imwheel, which can only configure mouse events in specific apps, and I want it to be equivalent to Ctrl Alt Left and Ctrl Alt Right in any app.

Is there another way? Or will I have to use compiz instead of metacity?


EDIT:
I figured with **easystroke** I can configure a static mousegesture for those buttons, so that way I can make button 8/9 go to desktop left/right.

---

### Post by afeasfaerw23231233 on 2009-09-23
Have you looked at this thread?
[http://ubuntuforums.org/showthread.php?t=132384](http://ubuntuforums.org/showthread.php?t=132384)

---

### Post by techstop on 2009-09-23
Even better is this thread;

[http://ubuntuforums.org/showthread.php?t=455656](http://ubuntuforums.org/showthread.php?t=455656)

btnx is a program that lets you configure your mouse buttons to do *anything*. And you don't need to hack up xorg.conf or anything else. Strongly recommended.

---

### Post by geoffm on 2009-09-25
I tried btnx, it seems good, I configured the mouse buttons, I ran btnx with sudo, but it doesn't work. I made my up and down buttons act as Ctrl Alt Left / Right, but it seems like the program doesn't catch the events...

---

### Post by LifeEnemy on 2009-10-09
btnx broke in an earlier version of Ubuntu  (8.10 i think), and apparently it's not going to be fixed. I also tried using it for a while, and it works for some things, but other times it totally fails or freezes my comp. I'm currently searching for an alternative.

---

