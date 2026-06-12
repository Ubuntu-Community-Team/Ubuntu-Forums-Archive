---
title: "prboom and lxdoom-x11 display problems"
date: 2005-10-11
forum: Gaming &amp; Leisure
---

### Post by eivind on 2005-10-11
Hi, folks

I've tried prboom and lxdoom-x11, and I am experiencing strange display problems. When I start up either game, I get a window which contains 3 game displays side by side, all identical. A 3-in-1 display, one could say. 
I have tried editing prboom.cfg and the lxdoom config file respectively, to change screen size, but that just changes the window size. I still get 3 game displays in one window.

So now I am playing lxdoom-svga, which works, but it would have been nice to have the x version working too. I have tried googling and searching the Ubuntu forums, to no avail. Has anyone experienced something similar, or does anyone have a tip?

Thanks in advance!


Cheers,

Eivind

---

### Post by MikeNick42 on 2005-10-15
I'm having the same problem.  My solution had been to run it at 1280 by 400 and only look at one screen.  I can't get lxdoom-svga to work because I don't have I/O permissions on libsvga.  Is there a way to fix that without doing a setuid root for lxdoom-svga?

Thanks,
Mike

---

### Post by eivind on 2005-10-17
I just followed the descriptions in /usr/share/doc/lxdoom-svga/README.Debian, so that means I run lxdoom as setuid root. As far as I know, that's the only to run lxdoom as a normal user. Anyway, it works. But I must confess I didn't see a security risk in running setuid root... Maybe lazy, but that's what I did.

Cheers,

Eivind

---

### Post by bernardfrancois on 2006-04-09
Did anyone make prBoom work properly? I can play it with MikeNick42's idea, but I don't enjoy playing it since its too small and too confusing. I would like to be able to play it full-screen.

If I play it windowed, all other window's colors appear to be inverted... Strange stuff.

---

### Post by bernardfrancois on 2006-04-12
Yesteday I installed the latest version (2.4.1) and it still has the same problem.
I noticed the problem's not there on my other computer, running ubuntu 5.10 instead of 5.04... Anyone who has any idea of the reason/solution of this?

---

### Post by MikeNick42 on 2006-05-02
I have it running fine on another computer with Breezy and after I reinstalled Ubuntu on the problematic computer, for reasons unrelated to doom, lxdoom worked fine on it.  As far as I know all my setting were still same so I don't know what caused the problem.

---

