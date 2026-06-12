---
title: "Quake Live does NOT work on Ubuntu 9.04."
date: 2009-09-29
forum: Game Specific Discussions
---

### Post by LeDechaine on 2009-09-29
If you've gotten it to work, prove it.

The XPI file won't install. Well, no, it does a FAKE install. Because when I restart Firefox (3.5.3), it asks me to install the plugin AGAIN.
So I can't download the game files.

And this infinite loop game is not the game I wish to play at the moment.

The only way I can install it is by running firefox as root. Because when I sudo firefox, the plugin installs, I restart firefox, and then I can download the game files. But guess what, I don't want to play Quake Live as root.

Anyone ever experienced the problem? I've searched, and it looks like i'm the only one with this problem. This is senseless.. I was using Ubuntu 9.04 with Firefox 3.0.13, which is the **default** firefox in Ubuntu 9.04, and this problem appeared. Why would I be the only one with this problem? And this problem is the only reason why I updated firefox. A desperate attempt at fixing this bug because the Quake Live website mentions that it should work from "Firefox 2.0+".

If you can help me, thanks in advance.

PS: I'm using Ubuntu 9.04 32-bit. And deactivating NoScript changes nothing.
Edit: Deactivating *every* plug-in I have in firefox does nothing, too. So it's **not** a conflict with a plug-in.

---

### Post by moster on 2009-09-29
Try to delete all cookies and history, everything. and restart firefox then try again. I think I remember some similar problems when linux version appear. Seems stupid but just try it.

---

### Post by LeDechaine on 2009-09-29
Well, the game contents are loading!

Looks like it had something to do with the fstab partition parameters set to "user", which meant **noexec**, which prevented the xpi file from doing something on my system!

If not, it's just a reboot that solved the problem.. But it sounds too "Windows" to be true. ;)

Thanks anyway!

---

### Post by LeDechaine on 2009-09-29
Hehe that's sick, I was struggling to install this and I didn't even knew if it would run, but i'm amazed, i'm playing this game on a Pentium 3 866 with 320 megs of ram, and an ATI Radeon 9250, in a 1024x768 window with all graphic options to the max, and there's no lag at all, except low (15+) FPS when there's action..
When running around, the FPS is more likely to range from 25 to 50+. (And never to go down 25 in 800x600)

Damn, it was laggy on my friend's P4 with WinXP and an onboard graphics card..!

Firefox just crashes when I try to go fullscreen, but whatever. For now, i'm happy! :D

---

### Post by moster on 2009-09-29
Very glad to hear that. :) But it is something that I certainly not expect. haha, now back to fragging :D

---

### Post by chrisjsmith on 2009-09-29
Works here but if I go full screen with the open-source driver it kills firefox straight away.  Something to do with a missing X extension (Xwindows sucks).  Can't get a backtrace either using gdb.  Grr!

Playing it in a tiny window is a pain.

Damn me for being a cheap-*** and using an ancient graphics card which is no longer supported by ATI (9600)

---

### Post by moster on 2009-09-29
> **chrisjsmith said:**
> Works here but if I go full screen with the open-source driver it kills firefox straight away.  Something to do with a missing X extension (Xwindows sucks).  Can't get a backtrace either using gdb.  Grr!

Playing it in a tiny window is a pain.

Damn me for being a cheap-*** and using an ancient graphics card which is no longer supported by ATI (9600)

Look at the bright side. When they eventually do get full 3d support for your card, you will not have to deal with proprietary vga drivers.

Look at this link, you are one tiny step from my ULTIMATE GOAL. And that is all drivers in kernel, nothing proprietary.
[http://www.phoronix.com/scan.php?page=news_item&px=NzUxNg]("http://www.phoronix.com/scan.php?page=news_item&px=NzUxNg")

---

### Post by chrisjsmith on 2009-09-30
> **moster said:**
> Look at the bright side. When they eventually do get full 3d support for your card, you will not have to deal with proprietary vga drivers.

Look at this link, you are one tiny step from my ULTIMATE GOAL. And that is all drivers in kernel, nothing proprietary.
[http://www.phoronix.com/scan.php?page=news_item&px=NzUxNg]("http://www.phoronix.com/scan.php?page=news_item&px=NzUxNg")

Good point.  TBH the open source drivers are actually pretty good, even if they do miss all the latest extensions and some of the performance.

---

