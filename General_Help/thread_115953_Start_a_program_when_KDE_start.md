---
title: "Start a program when KDE start"
date: 2006-01-11
forum: General Help
---

### Post by Alpha_toxic on 2006-01-11
I want to make some programs start when KDE starts and I somehow can't find how to do it :confused:... I'm sure it was here somewhere, but I don't have the time to look for it...
Please someone end my misery :).

---

### Post by MartinJ on 2006-01-11
You could create a link to the program in your Autostart directory:

/home/username/.kde/Autostart

Use right click -> Create New -> Link to Application

---

### Post by Alpha_toxic on 2006-01-11
"Yes, this was it!!!" :slaps his head:
10x :)

---

### Post by optotron on 2006-01-11
is there a way to start the programs minimized by default?

---

### Post by xMetaRidley on 2006-01-11
[QUOTE=optotron]is there a way to start the programs minimized by default?[/QUOTE]

You can use window-specific settings (in the window behavior dialog).  You can also use kstart if you want a command to start it minimized:

kstart --iconify command

---

### Post by optotron on 2006-01-12
[QUOTE=xMetaRidley]You can use window-specific settings (in the window behavior dialog).  You can also use kstart if you want a command to start it minimized:

kstart --iconify command[/QUOTE]


Ok thanks a lot =)

---

### Post by optotron on 2006-01-12
ah! I came up with another (related) question

If i'd like to start the program in the system tray only, can I do that without using window-specific behaviour?

---

