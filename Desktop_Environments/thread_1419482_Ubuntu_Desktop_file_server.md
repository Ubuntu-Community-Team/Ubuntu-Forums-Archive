---
title: "Ubuntu Desktop file server"
date: 2010-03-01
forum: Desktop Environments
---

### Post by DarkSotM on 2010-03-01
I'm putting together a computer in our wood-shop/studio as a general purpose web browser, music player, whatever machine.  I also wish to use this box as the local file server for music, movies, and what have you.

What I'm running into is such:
1. Ubuntu Desktop doesn't connect to the network until you log in (wireless at least, don't know about wired as there is no cable there)
2. Setting up samba is worse than getting teeth pulled

These are all Linux boxes on the network, so a client for windows isn't required but would be nice.  I am using a wireless connection right now, at least until I can get a Cat5 cable ran to the far corner of the building.  Because smb is mainly for windows I was thinking I could get rid of it and use something more UNIX like but I don't know which direction to look. Any ideas would help!

Thanks
DarkSotM

---

### Post by Agent ME on 2010-03-01
> **DarkSotM said:**
> 1. Ubuntu Desktop doesn't connect to the network until you log in (wireless at least, don't know about wired as there is no cable there)
Right-click the wireless icon, click "Edit Connections", "Wireless", your wifi network, "Edit...", and check the boxes for "Available to All Users" and "Connect Automatically". Problem solved.

> **DarkSotM said:**
> 2. Setting up samba is worse than getting teeth pulled
For a simple sharing set up that is just a few fixed folders, don't you just need to right-click them, click "Share" and click through a dialog box?

---

