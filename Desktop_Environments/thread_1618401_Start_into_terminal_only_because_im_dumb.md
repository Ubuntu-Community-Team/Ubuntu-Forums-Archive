---
title: "Start into terminal only because im dumb"
date: 2010-11-10
forum: Desktop Environments
---

### Post by Ocelot_P on 2010-11-10
Im using unbuntu 10.10, AMD 64 processor and nvidia graphics card, and everytime i start up the computer i am stuck in terminal only setting. I use startx and get this:

Parse error on line 3 of section Screen in file /etc/X11/xorg.conf
         "TwinView" is not a valid keyword in this section.
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found



I typed the TwinView into the /etc/X11/xorg.conf when trying to connect my laptop to the T.v. How do I undo/fix this shizz?

---

### Post by drs305 on 2010-11-10
From the terminal, you can edit the file as root:
```
sudo nano /etc/X11/xorg.conf
```

Use the cursor to move about the file, make your changes, then CTRL-x to save.

If you don't remember what changes you made, post the contents here.

---

