---
title: "Dueling soundcards"
date: 2005-12-15
forum: Desktop Environments
---

### Post by dto on 2005-12-15
One of my PCs has two soundcards installed -- a Soundblaster Live and an M-Audio 2496.

This machine dual boots Linux and that other OS. I'd like for Ubuntu to only load the es1371 driver for the Soundblaster card, and ignore the ice1712 driver for the M-Audio card (which I only want to use in Windows). It presently loads both.

What's the best way to achieve this?

---

### Post by 23meg on 2005-12-15
Try adding snd-ice1712 to your /etc/modprobe.d/blacklist file.

---

### Post by dto on 2005-12-15
That file didn't exist, but you definitely pointed me in the right direction. I had to put it in /etc/hotplug/blacklist.

Works great, and now I've learned a bunch of stuff on how hotplug works. :)

---

### Post by 23meg on 2005-12-15
Oh sorry, that was a typo; anyway happy that you got it working; any kernel module you put in that file will be blacklisted and not loaded on startup.

---

