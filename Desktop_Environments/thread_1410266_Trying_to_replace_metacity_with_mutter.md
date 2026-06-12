---
title: "Trying to replace metacity with mutter"
date: 2010-02-18
forum: Desktop Environments
---

### Post by Pasty745 on 2010-02-18
I am not sure if this is the correct section; so sorry if it isn't.  But I am trying to replace metacity with mutter on my laptop running ubuntu 9.10 x64, with ati 3200HD.  I have installed the packages, but when I try to use the "sudo mutter --replace" command I just keep getting the following error: 
Window manager warning: Log level 16: NOTE: Not using GLX TFP!

Could anyone tell me what I am doing wrong, and how to fix it?  Also, is there a way to check that it is being used (i.e. through the terminal or by some other method)?  Thanks in advance.

---

### Post by Dies on 2010-02-18
For one thing you're trying to run a window manager as root. There may be good reasons to do that, but none that I can think of.

Another thing is your graphics card (or more likely your drivers) apparently isn't up to the task, so if it does run for you I wouldn't expect good performance.

---

