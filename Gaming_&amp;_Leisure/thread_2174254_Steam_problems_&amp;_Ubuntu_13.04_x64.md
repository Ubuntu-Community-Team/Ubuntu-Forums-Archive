---
title: "Steam problems &amp; Ubuntu 13.04 x64"
date: 2013-09-13
forum: Gaming &amp; Leisure
---

### Post by acaciajnv on 2013-09-13
Greetings.

This morning I installed under Wine a windows client of Steam in order to download and install a couple of games that I can't have when I use Linux native client. I used 'PlayOnLinux' for that installation.

The problem is that now regular linux client can't start, it promps a message "Verifying installation" with a loading bar for a few seconds and then disapears, no Steam icon in system tray nor any instance in Unity bar. However, when I check system monitor I can see a Steam process running in background and compsuming 25% CPU load (In fact, 100% of one core, since this is a Quad-Core computer).

I have tried uninstalling PlayOnLinux, then Linux Steam and reinstall... but doesn't work. I won't like to purge all data and then download everything again (My SSD won't like that too)... so is there any other solution I am missing?

Thanks.

---

### Post by Shrek01 on 2013-09-13
Hi there.

I am having the same issue after today's upgrade of lightdm.  Steam uses the CPU 100% and it hangs.
I'm using 13.04 32bits and I have the latest nvidia driver.

So we are in the same boat.  I don't think it has anything to do with what you did this morning.

---

### Post by ELD on 2013-09-13
Fixes are here: [http://www.gamingonlinux.com/articles/steam-for-linux-is-a-little-messed-up-heres-the-temporary-fix.2416](http://www.gamingonlinux.com/articles/steam-for-linux-is-a-little-messed-up-heres-the-temporary-fix.2416)

---

### Post by Shrek01 on 2013-09-13
Thanks a lot.  That fixed it for me :D

---

### Post by Ste_JDM on 2013-09-14
Awesome thanks!

---

### Post by DarkAmbient on 2013-09-14
Anyone knows why this error occured? No error here, but it seemed to affect a lot of people. :-S

---

### Post by acaciajnv on 2013-09-14
I'm happy to see the problem got solved, sadly I just reinstalled Ubuntu this morning... however, the problem appeared again, just the same thing, and after upgrading my AMD/ATI graphic card drivers that issue just vanished.

As far as I could investigate yesterday, it was something about some issue with graphic-32b-libraries in a 64b enviroment, since Steam client and most games are 32b only. (Excluding some cases like Kerbal Space Program).

Too sad I haven't figured yet why this happened and didn't learn much about this.

---

