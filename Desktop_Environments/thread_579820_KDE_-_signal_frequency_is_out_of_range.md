---
title: "KDE - signal frequency is out of range"
date: 2007-10-18
forum: Desktop Environments
---

### Post by kooldino on 2007-10-18
I have a machine that originally ran Ubuntu Feisty Fawn.  I then installed KDE onto it.

Recently, I upgraded it to Gusty Gibbon.

Today, I was messing around trying to get compiz working under KDE.  The machine has a low end geforce 4, and I installed the 'nv' driver.  I also installed the xgl server (or at least attempted to).

Now, when I boot the machine, it eventually loads the graphical login screen.

Upon login to KDE, my monitor shows an error message - "signal frequency is out of range"

I tried editing xorg.conf and deleted the line that had 1024x768 in hopes that it would display in 800x600 so I can reconfigure things better.

The only thing that changed was that my login screen now became 800x600.  KDE still wouldn't display on my monitor.

I can, however still run GNOME.  

How can I get my KDE working again?

---

### Post by kooldino on 2007-10-18
The issue ended up being that the framebuffer was on when it needed to be off (I assume).


After doing a  sudo dpkg-reconfigure xserver-xorg and switching it to on, it worked again.

---

