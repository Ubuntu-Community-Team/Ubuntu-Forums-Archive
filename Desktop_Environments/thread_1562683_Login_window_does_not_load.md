---
title: "Login window does not load"
date: 2010-08-27
forum: Desktop Environments
---

### Post by danjl1100 on 2010-08-27
I installed Ubuntu 10.04 as a second OS on my XP machine (on a second partition). It worked fine for about a month, but this time when I booted up in Ubuntu, it showed the Ubuntu loading screen, then the desktop background picture and mouse, but it did not load the login window. I have no idea how to fix this, because most problems are about the entire X server not working, whereas my screen works. 

I tried pressing Ctrl + Alt + F1, stopping gdm, then running startx, which mostly worked, except the date and time status bar addons had an error loading and the task bar did not have any workspace icons on it. I would like to login the normal way to get back to my good old Ubuntu desktop, but the window does not want to load. I have restarted the computer multiple times, with the same result.

All help is appreciated! :D

---

### Post by danjl1100 on 2010-08-30
I figured out that the problem was that I had manually installed (and "make"-ed) gtk+ and zlib. I assume that they were interfering with other versions already installed, allowing the desktop to come up, but stopping the log in box from appearing.

---

