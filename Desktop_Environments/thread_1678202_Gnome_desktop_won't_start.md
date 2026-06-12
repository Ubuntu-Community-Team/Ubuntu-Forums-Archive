---
title: "Gnome desktop won't start"
date: 2011-01-29
forum: Desktop Environments
---

### Post by caribedude on 2011-01-29
Hi, I've recently updated to Ubuntu 10.10 and have run into some strange  problems. When I logged in for the first time, my windows lacked tool  bars (the X to close, minimize, etc), this wasn't the first time this  happened so I just finished what I had to do then used compiz to fix the  problem. When I changed the settings, they didn't take effect and the  computer started freezing and going slower so I rebooted. When I  rebooted the usual login screen appeared and when I entered my username  and password the Ubuntu login sound could be heard and I got a brief  flash of my desktop background. That was all I could see before the  screen turned black, showed some cryptic error messages (too fast to  read) and sent me to the login screen again. After a couple of tries I  managed to login, but there was no visible taskbar (it showed up when I  clicked where the taskbar was supposed to be) and when I opened firefox  the screen turned black and I got sent to the login screen again.
After that, I logged in using the terminal ran "sudo apt-get install  ubuntu-desktop" and "sudo apt-get install gnome-main-menu" but nothing  happened. I used the stop gdm/startgdm trick but nothing happened  either. The only thing that managed to do something was the "startx"  command. It showed some error messages (basically display 0 was in use  by something; I don't know what) so I ran "sudo startx -- :1" to switch  the x server. This made login as the root user. Everything there worked  perfectly. I tried logging in with failsafe-gnome and it also worked.  This leads me to believe the problem has something to do with some  configuration I have on gnome. Any sugestions, tips or ideas are  welcome.

---

