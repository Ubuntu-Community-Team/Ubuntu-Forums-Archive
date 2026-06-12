---
title: "How to switch out of Fullscreen Games"
date: 2006-09-17
forum: Gaming &amp; Leisure
---

### Post by Jordash on 2006-09-17
Hey all,

Well I got alot of games working like Cube and Enemy Territory, my problem is, i'm a Multi-tasker so I can't figure out how to switch between different programs once a game like Enemy Territory is open.  (e.g. I try pressing alt+tab, or ctrl+esc) to get out of the game without exiting but I can't figure out what keystrokes will return me to desktop without exiting the game entirely.

Any ideas?

Thanks,

Jordan

---

### Post by coastdweller on 2006-09-17
alt+enter?

> **Jordash said:**
> Hey all,

Well I got alot of games working like Cube and Enemy Territory, my problem is, i'm a Multi-tasker so I can't figure out how to switch between different programs once a game like Enemy Territory is open.  (e.g. I try pressing alt+tab, or ctrl+esc) to get out of the game without exiting but I can't figure out what keystrokes will return me to desktop without exiting the game entirely.

Any ideas?

Thanks,

Jordan

---

### Post by Jordash on 2006-09-18
That didn't seem to work :( Anyone else run into this problem?

---

### Post by fatsheep on 2006-09-18
Yea I've run into this problem in every full screen game I play.  I even filed a support request about it a while back:

[https://launchpad.net/distros/ubuntu/+ticket/1711](https://launchpad.net/distros/ubuntu/+ticket/1711)

---

### Post by haxer on 2006-09-18
Hmm.. no more easy version? like .. something that you dont have to compile like source code and stuff?

---

### Post by HAARP on 2006-09-18
add this
```
Option		"AllowDeactivateGrabs"	"1"
```
to your xorg.conf under **Section "ServerFlags"** and press [ctrl]+[alt]+[backspace] to restart X
**[ctrl]+[alt]+[keypad-divide]** should now enable you to kill the mouse grab and alt-tab out of games. (sometimes)
However, this doesn't work well and sometimes you can't go back.

---

