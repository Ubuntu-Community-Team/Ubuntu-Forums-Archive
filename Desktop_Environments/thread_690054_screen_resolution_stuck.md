---
title: "screen resolution stuck"
date: 2008-02-07
forum: Desktop Environments
---

### Post by dbrower256 on 2008-02-07
I have a problem with my screen resolution.  After I turned off the computer and later restarted it, the screen resolution is at 800x600.  When I try to change it, I only get two options.  I couldn't find another posting on this problem, but I'm sure other people have come across it?  What causes this and what should I do about it?  As a note, I'm using Ubuntu 7.10 Server.

Daniel

---

### Post by renzokuken on 2008-02-07
what grafix chip are you using? try running the command

```
sudo dpkg-reconfigure xserver-xorg
``` and add the desired resolutions that way

---

### Post by mguthriejr on 2008-02-26
yea that worked for me too i just tried it

---

