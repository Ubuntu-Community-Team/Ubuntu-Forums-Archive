---
title: "How do I use wine to install from CD-ROM?"
date: 2007-04-24
forum: Desktop Environments
---

### Post by volksolwagen57 on 2007-04-24
i installed wine and used winecfg to autodetect my drives. i closed this and went to the cd in the dvd drive and browsed to the Setup.exe file and double clicked it. nothing happens. i tried this a few times and then tried it though the terminal. i type wine /media/cdrom1/Setup.exe and there is a small pause when i press enter and then again, nothing happens. what did i miss. can someone help me with this please? i am actually trying to install RollerCoaster Tycoon, the original game for windows.
i appreciate your help in advance.

---

### Post by dcstar on 2007-04-24
> **volksolwagen57 said:**
> i installed wine and used winecfg to autodetect my drives. i closed this and went to the cd in the dvd drive and browsed to the Setup.exe file and double clicked it. nothing happens. i tried this a few times and then tried it though the terminal. i type wine /media/cdrom1/Setup.exe and there is a small pause when i press enter and then again, nothing happens. what did i miss. can someone help me with this please? i am actually trying to install RollerCoaster Tycoon, the original game for windows.
i appreciate your help in advance.

cd to the directory where the setup is, and then just use "wine setup.exe".

Wine may not like the Linux file path with the "/" characters, I think you need to specify the DOS equivalent path.

---

### Post by grindboy on 2007-12-28
I found this post while searching for a solution to the same problem. I had Wine autodetect my drives. Now when I find a .exe file I can just right click on it and ask for it to be run through wine! YAY! Nice program! Now I can use fireworks MX a program I'm much more familier with than GIMP

---

