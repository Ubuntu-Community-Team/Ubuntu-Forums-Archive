---
title: "Super tux kart problem"
date: 2010-11-03
forum: Gaming &amp; Leisure
---

### Post by rudysuryanto on 2010-11-03
When I am playing game super tux kart, then suddenly system hang, how to solve this? Thank's.

---

### Post by Noraphalem on 2010-11-04
Please run the game from the terminal and post us the output.  Alt + F2 to open the run dialog  Type in gnome-terminal and press Enter  Type into the terminal supertuxkart and press  Enter  Open the game in windowed mode to see what's going on.

---

### Post by rudysuryanto on 2010-11-05
rudy@rudy-desktop:~$ supertuxkart --log=terminal
Data files will be fetched from: '/usr/share/games/supertuxkart/'
Highscores will be saved in '/home/rudy/.supertuxkart/highscore.data'.
WARNING: Music not playing when it should be. Source state: 4116
X Error of failed request:  BadDrawable (invalid Pixmap or Window parameter)
  Major opcode of failed request:  137 (XFree86-DRI)
  Minor opcode of failed request:  9 ()
  Resource id in failed request:  0x4200011
  Serial number of failed request:  7380
  Current serial number in output stream:  7380
AL lib: ALc.c:1879: exit(): closing 1 Device
AL lib: ALc.c:1808: alcCloseDevice(): destroying 1 Context(s)
AL lib: ALc.c:1420: alcDestroyContext(): deleting 33 Source(s)
AL lib: ALc.c:1818: alcCloseDevice(): deleting 25 Buffer(s)

---

