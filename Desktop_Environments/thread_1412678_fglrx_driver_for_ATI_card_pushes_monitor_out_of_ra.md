---
title: "fglrx driver for ATI card pushes monitor out of range"
date: 2010-02-21
forum: Desktop Environments
---

### Post by KingofthePlebs on 2010-02-21
Hey guys, this is my first post in the community, as I just installed Ubuntu 9.10 for the first time this weekend. I am certainly no computer expert, but I'm hoping that through learning to use and utilize Ubuntu my knowledge will increase.

I am running Ubuntu 9.10, my video card is ATI Radeon HD 3600

Heres my issue:

When I originally attempted to enable desktop effects, I was told that I was unable to do so. Not being one to rush to ask a question, I tried to figure out the issue, and it seemed to be that I needed to install the fglrx driver available for ATI cards- a simple enough fix. I installed the driver, and rebooted my machine, and everything seemed to be fine- the initial splash page came up- but immediately afterwards (presumably when I reached the login screen) My monitor went out of range. 

Not being strong in coding, I was unable to figure out a way to remove the driver without a GUI (though I think I very well could have), so I had to uninstall and reinstall (no sweat, I hadn't really started anything yet). However, its obvious that the fglrx driver is what blew it out of range.

My question is, is there anything I can do to get this driver to work on my machine? I found similar questions but they all seemed either to be slightly different from my issue or recommended changing the .xorg file, which does not exist in 9.10. Please help, thanks in advance! ):P

---

### Post by aarons6 on 2010-02-22
you certainly do have an xorg.conf file..
install the drivers from  and drop down to a term.
type in aticonfig --initial to install the drivers into the xorg.conf file.

are you using the open drivers or the ati ones?

---

