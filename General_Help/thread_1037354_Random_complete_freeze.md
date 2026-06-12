---
title: "Random complete freeze"
date: 2009-01-11
forum: General Help
---

### Post by Reactor5 on 2009-01-11
After a certain period of time on, my system will completely freeze.  The caps lock light will blink on and off when it's doing this, and the only way to get it to continue is to do a hard reset of the computer.  Where should I start looking for error messages/fixes?

Ubuntu 8.10
Lenovo Thinkpad T61

---

### Post by jgoguen on 2009-01-11
I've been having this issue myself randomly.  It seems to have stopped when I stopped using the wl driver for my Broadcom wireless card.  You could file a kernel bug the next time it happens.  The next time it happens, immediately after rebooting, run the command **ubuntu-bug -p linux**.  This will gather some information and create a bug report.  

Also, the next time this happens, try some magic SysRq keys before forcing a reboot.  If it works, the laptop should restart on its own.  Find a key labelled SysRq (maybe Sys Rq, maybe all lower-case) and determine if you need to push the Fn key for it.  If you do, SysRq will be outlined the same as the Fn key.  To send SysRq commands, push Alt+SysRq (including the Fn key if needed) and each of these letters, in order, with 3-4 seconds between each letter: R, E, I, S, U, B.  If your system is hung up hard, like mine was, nothing will happen.  Mention whether or not the SysRq keys did anything in our bug report.

---

### Post by Cope57 on 2009-01-11
Sounds like desktop effects, but I could be wrong.
I have noticed most lock-ups were laptop issues and compiz (desktop effects) enabled.

---

### Post by electrogeist on 2009-01-11
run memtest overnight

---

### Post by RJARRRPCGP on 2009-01-16
Run **mprime** overnight.

---

