---
title: "Enemy Territory: Quake Wars problem"
date: 2008-10-10
forum: Gaming &amp; Leisure
---

### Post by utmost on 2008-10-10
Hi!

I have installed ETQW according to the instructions posted at

[http://gaming.gwos.org/doku.php/guides:64bit:etqw](http://gaming.gwos.org/doku.php/guides:64bit:etqw)

Everything went fine except for a few error messages during the pre-installation phase - these lines:

sudo aptitude update && sudo aptitude safe-upgrade
sudo aptitude install ia32-libs

The terminal said that a few packages were held back (or something).

Anyway, I pressed on and everything else went fine. The game installed and then I followed the instructions to create a launcher, which didn't work (no shortcut appeared on the desktop or applications/games menu). However, when typing ETQW into the terminal the 1st time, the game started and played and all was good!

Then I shut it down, did a few updates recommended by the OS and restarted the computer. Since then I can enter the game by typing ETQW into the terminal but all mouse functionality ceases immediately and does not work again until a reboot is completed.

This is bad. I thought ETQW could be an example of a reasonably modern game that runs on Linux but if it does, it's playing hard to get. Please help!

---

### Post by Perfect Storm on 2008-10-16
[Moved to Gaming & Leisure]

It may due to Compiz.

Try this;

```
metacity --replace
etqw
```

---

