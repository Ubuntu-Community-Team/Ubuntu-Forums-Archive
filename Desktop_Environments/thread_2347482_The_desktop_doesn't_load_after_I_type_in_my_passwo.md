---
title: "The desktop doesn't load after I type in my password"
date: 2016-12-25
forum: Desktop Environments
---

### Post by redmage123 on 2016-12-25
Hello all,

I'm running Ubuntu 16.04 (64 bit) on an Intel I7 CPU system. It's been working fine until tonight.
The problem that I'm having is that when I type in my password on the graphical screen, it just throws
me back to the login screen again and doesn't load my desktop.  The problem isn't my password as it 
doesn't give me an 'invalid password' string.  

I've been trying to debug this but I can't seem to find the magic clue.  I've checked in /var/log/Xorg.0.log and in 
.xsession-errors in my home directory.  

Nothing seems to stand out.   How do I go about debugging this problem?  Obviously something in my state has changed but I'm not 
able to figure out what it is.  Also, I don't get any sort of error message from the graphical interface as to why it isn't working.  

I'm also not up on the latest developments in 16.04.  Does it still run X Windows?  I'm assuming that the lightdm application the X server?
Is /usr/bin/xinit being run at all? How does Unity fit into this puzzle.  

What i'd really also like to know is where to go look for the error message that will tell me why I'm not getting my desktop any longer. 

Any help appreciated.

---

