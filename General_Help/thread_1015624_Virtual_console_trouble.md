---
title: "Virtual console trouble"
date: 2008-12-19
forum: General Help
---

### Post by killersnowgoon on 2008-12-19
I can't access any virtual consoles. the system monitor shows 6 getty programs running on tty1-6, but ctrl+alt+f1 (or f2-6) doesn't switch to them. the only way i can access them is via the command "sudo telinit 1", and then using ctrl+alt+f1. i can also access them during the booting process, but once X starts up i cant. anyone have any ideas? :confused: :confused: :confused:

btw, i'm using intrepid 64bit on a sony vaio vgn-fz490

---

### Post by dcstar on 2008-12-19
> **killersnowgoon said:**
> I can't access any virtual consoles. the system monitor shows 6 getty programs running on tty1-6, but ctrl+alt+f1 (or f2-6) doesn't switch to them. the only way i can access them is via the command "sudo telinit 1", and then using ctrl+alt+f1. i can also access them during the booting process, but once X starts up i cant. anyone have any ideas? :confused: :confused: :confused:

btw, i'm using intrepid 64bit on a sony vaio vgn-fz490

You may well find that the laptop remaps the FN keys and you need to use a special key to use them.

---

### Post by killersnowgoon on 2008-12-19
> **dcstar said:**
> You may well find that the laptop remaps the FN keys and you need to use a special key to use them.

wouldnt that mean it wouldnt work in runlevel 1 either? and how would i check that? my keyboard settings are 104 key generic keyboard, US layout.

---

### Post by dcstar on 2008-12-19
> **killersnowgoon said:**
> wouldnt that mean it wouldnt work in runlevel 1 either? and how would i check that? my keyboard settings are 104 key generic keyboard, US layout.

Sorry, I don't know. Do a forum search for your hardware or anything similar.

---

### Post by killersnowgoon on 2008-12-19
Couldn't fine anything else =/
Well thanks for the help anyways. Anyone else have any ideas?

---

### Post by killersnowgoon on 2008-12-20
Still can't figure this out. Help?

---

### Post by killersnowgoon on 2008-12-21
Bump for help

---

### Post by Reilithion on 2009-01-15
killersnowgoon, are you, by any chance, using a dual-head setup on your system?  Does your xorg.conf file have more than one monitor entry?  I've been having trouble switching to virtual consoles ever since I edited my xorg.conf file to use both of my graphics cards.  Solutions available on the web are... sparse.

---

### Post by killersnowgoon on 2009-01-16
no, im not. and i recently did a fresh install to a new hard drive, which of course fixed the problem. i wish i could help.

---

### Post by Reilithion on 2009-01-16
Thank you, killersnowgoon.  I'll keep looking.

---

