---
title: "How can I change my default session manually?"
date: 2008-04-30
forum: Desktop Environments
---

### Post by themightymegatron on 2008-04-30
Here's the story. I recently upgraded from Gutsy 7.10 to Hardy 8.04, like just about everyone else here. Except for my wireless card and compiz, everything was working fine. I got the WNIC running, but I still couldn't figure out how to get compiz up and going. After a quick google search I found [this page.]("http://www.ubuntu1501.com/2007/08/compiz-fusion-in-fiesty-with-xgl.html") Even though it was for feisty and a Dell notebook, I tried to get it running on Hardy anyway (yeah, I know, bad idea) because even though I run a Compaq Presario V26008WM, I have the same graphics card (ATI Mobility Radeon XPRESS 200M). 

Well, I did as it said, creating/installing all of the files needed. Thinking it was going to work (like a fool), I changed my default session in the session manager from "gdm" to "xgl". Bad idea. When I rebooted it loaded up to the login screen and then I get a message that says "Authentication Failed" and it keeps popping up no matter how many times I click "OK". All I can do is either click OK or hit the power button on my machine. Won't let me do anything else. 

Thinking fast I downloaded the Hardy Live CD straight from the ubuntu website (using my mother's Desktop PC), ripped it to a disk, and then tried to boot it on my Compaq. It wouldn't go. 16 reboots later, it still skipped the CD and went right to Grub. I gave up and decided to try my Gutsy Live CD just in case. I managed to get it up and running, got into my Hardy filesystem and deleted the files **/usr/local/bin/startxgl.sh** and **/usr/share/xsessions/xgl.desktop** that the tutorial had me create. I rebooted from my HDD and I still got the "Authentication Failed" message when it loaded GDM. I've reloaded my live CD and am trying to figure out a way to fix this without a reinstall. I'm pretty sure that if I change whatever file it is that controls the default session from XGL back to GDM then things should be fine. I'm not 100% on that though. 

If I'm not mistaken I need to be looking somewhere in **/etc/X11/** for whatever file I need, but I'd rather wait for a response before I start poking around again. 

For all I know I'm way off on this one though, so any help would be greatly appreciated guys! Thanks in advance!

---

### Post by warp99 on 2008-04-30
> **themightymegatron said:**
> Here's the story. I recently upgraded from Gutsy 7.10 to Hardy 8.04, like just about everyone else here. Except for my wireless card and compiz, everything was working fine. I got the WNIC running, but I still couldn't figure out how to get compiz up and going. After a quick google search I found [this page.]("http://www.ubuntu1501.com/2007/08/compiz-fusion-in-fiesty-with-xgl.html") Even though it was for feisty and a Dell notebook, I tried to get it running on Hardy anyway (yeah, I know, bad idea) because even though I run a Compaq Presario V26008WM, I have the same graphics card (ATI Mobility Radeon XPRESS 200M). 

Well, I did as it said, creating/installing all of the files needed. Thinking it was going to work (like a fool), I changed my default session in the session manager from "gdm" to "xgl". Bad idea. When I rebooted it loaded up to the login screen and then I get a message that says "Authentication Failed" and it keeps popping up no matter how many times I click "OK". All I can do is either click OK or hit the power button on my machine. Won't let me do anything else. 

Thinking fast I downloaded the Hardy Live CD straight from the ubuntu website (using my mother's Desktop PC), ripped it to a disk, and then tried to boot it on my Compaq. It wouldn't go. 16 reboots later, it still skipped the CD and went right to Grub. I gave up and decided to try my Gutsy Live CD just in case. I managed to get it up and running, got into my Hardy filesystem and deleted the files **/usr/local/bin/startxgl.sh** and **/usr/share/xsessions/xgl.desktop** that the tutorial had me create. I rebooted from my HDD and I still got the "Authentication Failed" message when it loaded GDM. I've reloaded my live CD and am trying to figure out a way to fix this without a reinstall. I'm pretty sure that if I change whatever file it is that controls the default session from XGL back to GDM then things should be fine. I'm not 100% on that though. 

If I'm not mistaken I need to be looking somewhere in **/etc/X11/** for whatever file I need, but I'd rather wait for a response before I start poking around again. 

For all I know I'm way off on this one though, so any help would be greatly appreciated guys! Thanks in advance!

Linux is a component OS so you don't need reinstall everything, just the components that are giving you a problem. I believe you made some modification to one of the gdm files, so we'll just give you new ones. Now when you get to the failed login press crtl+alt+F2 to get to a console and login, then issue the following:
```
sudo apt-get remove --purge gdm
```
this is going to remove all of the gdm components including the config files. Now it may ask to remove the ubuntu-desktop, but this is only a meta package and won't actually remove the desktop just the meta package. Once that's done then:
```
sudo apt-get install gdm
```
issue a 'sudo reboot' and this should place you back to a default gdm login.

---

### Post by themightymegatron on 2008-04-30
> **warp99 said:**
> Linux is a component OS so you don't need reinstall everything, just the components that are giving you a problem. I believe you made some modification to one of the gdm files, so we'll just give you new ones. Now when you get to the failed login press crtl+alt+F2 to get to a console and login, then issue the following:
```
sudo apt-get remove --purge gdm
```
this is going to remove all of the gdm components including the config files. Now it may ask to remove the ubuntu-desktop, but this is only a meta package and won't actually remove the desktop just the meta package. Once that's done then:
```
sudo apt-get install gdm
```
issue a 'sudo reboot' and this should place you back to a default gdm login.

Thank you sooooo much. I know it's hard to really help someone with these things when you can't be there to see it first hand, lol. I'm gonna try that now. I just got it pulled up to the bash prompt so I'm ready to go. I'll update here in a bit! Thanks again!

---

### Post by themightymegatron on 2008-04-30
Okay, it worked. Sort of... I did as you said and as promised it brought me back to a working login screen. However, when I logged in it acted like it was loading the desktop, and in fact I even got a cursor and the bottom panel loaded up, but then it hitched up on me, so I rebooted. 

One thing I noticed was that when I reinstalled GMD, the size of the install was about 4 MB smaller than the size of the packages I removed. It did ask me to remove the ubuntu-desktop, so I said 'yes'. I'm going to reboot and try to install the desktop package from bash and see what success I have.

Thanks again!

---

### Post by themightymegatron on 2008-04-30
Alright! So, when I went in and reinstalled ubuntu-desktop and rebooted I still got the lockup issue. I reboot again, then ran from the command line:

> sudo apt-get remove --purge ubuntu-desktop

followed by:

> sudo apt-get install ubuntu-desktop

at which point I was sure that that was going to reproduce the glitch again, so on a whim I ran:

> sudo apt-get autoremove

then

> sudo apt-get autoclean

from there, I rebooted, double checked to see that Gnome was the default session, and logged in. The result?

Well, the result is that warp99 is one bad mother ******, haha. Thanks again for all the help. I'd have been so danged lost if you hadn't been here man!

---

