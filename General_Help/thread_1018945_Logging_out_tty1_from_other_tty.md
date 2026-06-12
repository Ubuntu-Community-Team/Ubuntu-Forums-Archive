---
title: "Logging out tty1 from other tty"
date: 2008-12-22
forum: General Help
---

### Post by tiburcillo on 2008-12-22
Hello,

I'm having trouble logging out a console user from another tty/pts session. 

Problem: When logging in I automatically start a program (XBMC). It's still kind of buggy and sometimes it crashes, so I have a remote control to kill the process. After it is killed you just see a bash prompt on the screen. I need something to log out, so the user logs in again automatically and restarts the program.

just calling a script with exit doesnt work since the lirc daemon on the background is no running under tty1

Please gimme a hint! :)

---

### Post by Xiong Chiamiov on 2008-12-24
Why not just run the process again, or switch to the appropriate TTY and log yourself out?

---

