---
title: "Really mess up with the resolution of my machine"
date: 2008-09-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ralfaro10 on 2008-09-16
Greetings all,

This is the situation:

A couple of days ago I installed Burning crusade for my machine. I have a Dell Inspiron 1520 with a Intel Media Accelerator x3100 as video card and installed on it is the Ubuntu 8.04 Hardy Heron. Since I installed it, i have a lot of issues: 
1-When I tried to open the game, it reduces the resolution from  1280 x 768 to 1024 x 768. This one seems to be normal according with the resolution of the game. Bottom line is that when I close the game, it doesn't return back to the original setup for the resolution. I have to change it back manually but when I do that, machine hangs and doesn't do anything else in a long time, I have to restart it manually
2-Now, when I restart the machine it gets back to the 1280 x 768; however, both of the bars on the screen (the one below that shows the minimized windows and such and the one above that shows the application, menus, clock and more) are messed up, in a complete disorder and the worst thing is that if i tried to open a video here, it gets a white screen and hangs, doesn't do anything else and as well, i have to restart the machine manually

The most logical step could be to uninstall the game; however, the problem is still on the machine and don't know what to do

Any suggestions, I'd really appreciate them

Thanks!

---

### Post by natehall on 2008-09-17
Open a terminal and type in

 man xstart

 It gives some useful information that might help you solve the issue. Another idea to at least see what's going on is System> Administration>System log>Xorg.o.log
that will show the screen setting history.

---

