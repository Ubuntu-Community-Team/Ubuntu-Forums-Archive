---
title: "Starting up a command in Terminal window"
date: 2012-05-08
forum: Desktop Environments
---

### Post by lucken on 2012-05-08
I have an application that runs in the Therminal Window: ./magicq
 
But how can i:
- make a shortcut to the desktop that starts this application. When i rightclick on the application and create a shortcut, then nothing happens when clicking on the shortcut.
 
- how can i let the same appliaction starting automatically when booting the PC ?

---

### Post by LewisTM on 2012-05-08
Right-click on the desktop and choose 'Create launcher'.
Fill in the info. For the command, use the full pathname (not ./magicq). You can also specify the working directory. 
Check 'Run in terminal'.

The simplest way to start this at login is to copy the launcher to ~/.config/autostart

Cheers!

---

