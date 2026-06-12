---
title: "Need helping replacing the chosen Screensaver"
date: 2007-02-22
forum: Desktop Environments
---

### Post by shoki on 2007-02-22
Hello All,

I was wondering if somebody could help me locate the config file that stores the currently selected screensaver.

I picked a 3D one that causes X to crash. I don't need any 3D on this box so I just want to replace whatever is in there now with "blank-only".

The only file I can find is 
/home/shoki/.gconf/apps/gnome-screensaver/%gconf.xml

problem is that even though I can edit this file when I go back into the screensaver program it seems to overright this file with the previous (crashing) screensaver.

Thank you for your time and help,
--Shoki

---

### Post by shoki on 2007-02-22
Ah good I found it.

gconf-editor from the terminal hooked me right up.

Thank you,
--Shoki

---

