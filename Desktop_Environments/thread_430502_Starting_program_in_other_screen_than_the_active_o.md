---
title: "Starting program in other screen than the active one"
date: 2007-05-02
forum: Desktop Environments
---

### Post by mach777 on 2007-05-02
I am using xubuntu and xfce, and running 4 different screens.

I want to make a startup script that I can click to startup a host of applications, and send them to my different screens. For example, on one screen I want a terminal, one another screen I want a firefox browser, etc. My development environment has alot of programs I want to launch, and it takes quite some time to set it up everytime I boot my computer.

I guess what I'm asking is:

**What is the command to launch an application in a screen other than the active (first) one?**

Also, I am using up way too little memory!

Since I switched to linux I am hard pressed to top 500 meg, and I have 2gig in the machine. ;) All that ram going to waste, buhu.

---

### Post by hartz on 2007-05-02
Interestingly my RSS feeder recently alerted me to a few applications which would claim to automatically "restore" a window's attributes, such as it's position on your desktop, when the window appears.

I'll go and try to find the names as I did not at the time think to store it for future reference. :-)

---

### Post by hartz on 2007-05-02
I'm still looking, but remember that many X11 compliant programs support the "-geometry" setting.

try:
xterm -geometry 80x25+100+100
konqueror -geometry 800x600+50+50

Vary the items to see how they work.  The first two values specify size of the window, and the last two values an ofset from the screen's logical (X,Y)=(0,0) point.

---

### Post by hartz on 2007-05-02
OK, I found this: [http://ubuntuforums.org/showthread.php?t=75749](http://ubuntuforums.org/showthread.php?t=75749)

---

### Post by mach777 on 2007-05-02
> **hartz3 said:**
> OK, I found this: [http://ubuntuforums.org/showthread.php?t=75749](http://ubuntuforums.org/showthread.php?t=75749)

thanks i'll check it out

---

