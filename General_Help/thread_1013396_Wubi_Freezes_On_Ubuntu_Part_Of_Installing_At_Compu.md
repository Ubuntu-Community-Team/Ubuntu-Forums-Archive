---
title: "Wubi Freezes On Ubuntu Part Of Installing At Computing The New Partitions (100%)"
date: 2008-12-16
forum: General Help
---

### Post by Khaos139 on 2008-12-16
I have installed Ubuntu on my Dell Inspiron 1000, I have 223mb of ram so I continued the installation any way. It finished, I restarted and went into Ubuntu, then the Ubuntu installation starts. It gets up to...
```

Checking The Installation

Checking The Installation
////////////100%/////////
Computing The New Partitions
```

The code thing above is just supposed to represent the window.

It just stays like that, I can still move my mouse but the Installation doesn't continue...

Please help


EDIT: Now it completely froze, I think I am gonna restart it, delete ubuntu, and install Xubuntu
[B]
EDIT2: Xubuntu is installing fine, here's my question now, can I use the command line way to get gnome or kde, I like that interface better, since the installer already installed Xubuntu, will 223mb of ram be able to run the other interfaces?

EDIT3: Its been stuck at 0% on Installing System, Formating Swap Space In Partition #1 (Location), and its just stuck there, I can move my mouse but the little light that normally flashes when something is effecting the hard drive, but it stopped... what should I do? Restart?[/B]

---

### Post by DieB on 2008-12-16
ever tried it with the alternate-cd ? that should help it otherwise install ubuntu-desktop via:

sudo apt-get install ubuntu-desktop

---

### Post by Khaos139 on 2008-12-16
> **DieB said:**
> ever tried it with the alternate-cd ? that should help it otherwise install ubuntu-desktop via:

sudo apt-get install ubuntu-desktop

No because I am using the Wubi way so I don't think it would work

For Xubuntu

Its been stuck at 0% on Installing System, Formating Swap Space In Partition #1 (Location), and its just stuck there, I can move my mouse but the little light that normally flashes when something is effecting the hard drive, but it stopped... what should I do? Restart?

---

### Post by abn91c on 2008-12-16
> **Khaos139 said:**
> I have installed Ubuntu on my Dell Inspiron 1000, I have 223mb of ram so I continued the installation any way. It finished, I restarted and went into Ubuntu, then the Ubuntu installation starts. It gets up to...
```

Checking The Installation

Checking The Installation
////////////100%/////////
Computing The New Partitions
```

The code thing above is just supposed to represent the window.

It just stays like that, I can still move my mouse but the Installation doesn't continue...

Please help


EDIT: Now it completely froze, I think I am gonna restart it, delete ubuntu, and install Xubuntu
[B]
EDIT2: Xubuntu is installing fine, here's my question now, can I use the command line way to get gnome or kde, I like that interface better, since the installer already installed Xubuntu, will 223mb of ram be able to run the other interfaces?

EDIT3: Its been stuck at 0% on Installing System, Formating Swap Space In Partition #1 (Location), and its just stuck there, I can move my mouse but the little light that normally flashes when something is effecting the hard drive, but it stopped... what should I do? Restart?[/B]

I have the very same laptop, if you upgrade to 512mb ram, the max for the inspiron 1000 you can get kubuntu, no compiz because the default sis video card does not suppport 3D, other that that it will be a lot faster running kubuntu than XP with 512mb ram, also max lcd resolution will be same as Xp 1024x768. For DVD playback you may need to add the medibuntu repositories and get the dvd codecs libraries.
By the way reboot to windows first then restart from there to ubuntu, also did you defrag windows  first?

---

### Post by ago on 2008-12-19
Yes, you need more memory.

---

### Post by Khaos139 on 2009-01-02
> **abn91c said:**
> I have the very same laptop, if you upgrade to 512mb ram, the max for the inspiron 1000 you can get kubuntu, no compiz because the default sis video card does not suppport 3D, other that that it will be a lot faster running kubuntu than XP with 512mb ram, also max lcd resolution will be same as Xp 1024x768. For DVD playback you may need to add the medibuntu repositories and get the dvd codecs libraries.
By the way reboot to windows first then restart from there to ubuntu, also did you defrag windows  first?

Yea I defraged it and, I eventually just installed kubuntu over the hard drive, it worked without any problems concerning ram, it was fast to my suprise, but for the life of me I couldn't get and working driver for the wireless card, eventually, I decided to just reinstall install windows, and what do ya know, windows is working fast, I may go back to kubuntu but ill have to reset the resolution for it.

If you can find out how to get the wireless card working I'd appreciate it

Thx

---

