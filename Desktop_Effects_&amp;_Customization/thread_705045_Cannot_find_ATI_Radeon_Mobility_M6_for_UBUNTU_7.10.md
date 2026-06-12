---
title: "Cannot find ATI Radeon Mobility M6 for UBUNTU 7.10"
date: 2008-02-22
forum: Desktop Effects &amp; Customization
---

### Post by drywood on 2008-02-22
Hello, I need help in the configuration of the VGA card.

Computer: Flybook A33i
Scheda video: ATI Radeon Mobility M6 16 MB VRAM
OS: Ubuntu 7.10

I found another discussion in this forum about a similar context.
These are my first steps with Linux!
So what is xorg? should I install it?

The discussion is this:

[http://ubuntuforums.org/showthread.php?t=587039](http://ubuntuforums.org/showthread.php?t=587039)

years and years of DOS experience, but I couldn't understand that advices.

Anyone can help me?

This is my final target: use the dual monitor.

Thank you.

---

### Post by em3raldxiii on 2008-02-23
First off, just to give you a little background:

ATI videocards have been traditionally more difficult to configure in Linux operating systems (including Ubuntu) than nVidia cards.  Partly this is due to ATI's lack of open-source drivers and such.  Recently, ATI was purchased by AMD (makers of the Athlon processors), and ATI released some of their code to open-source development.  This has resulted in better support (this is very new, only a few months now).  Before too long, I expect support for Linux by ATI video cards will probably be better than that for nVidia.

Now, in order to get your card to work correctly, you are going to need to install the appropriate driver (you should have the open-source driver already installed), and then you probably will have to configure it.

As far as xorg is concerned, it is installed along with Ubuntu to facilitate the graphical user interface (see your other post where I explain further).

From what I can tell, the proprietary driver for the Radeon series doesn't support your specific card, but that could be old information and may not be true.

I'm at work right now and can't help a heck of a lot, but I hope this info will steer you in the right direction. :D

---

### Post by drywood on 2008-02-23
Thank you em3raldxiii, your advices help me to take the right way.
I found the driver for linux on the ATI/AMD site (50 MB).
Maybe that will work.

Don't worry about it: I don't want to take much time of yours, and now also I must stop with this problem until tonight.

Then I'll try with the ATI drivers.
Thank you and have a good day.

If anyone has got any other advice, please reply here.

Thanks.

---

### Post by fallsoff on 2008-02-23
Hi
I have dell c610 with same ati card. No problems with Gutsy, I just loaded the OS, set the resolution and it is fine__no dual monitors though. W2k to xp was much harder just because of the damned m6 gpu. That was a nightmare.
best 
fallsoff

---

### Post by drywood on 2008-02-23
> **fallsoff said:**
> __no dual monitors though

Thank you fallsoff. This is my problem:
The two monitors displays the same screen.

---

