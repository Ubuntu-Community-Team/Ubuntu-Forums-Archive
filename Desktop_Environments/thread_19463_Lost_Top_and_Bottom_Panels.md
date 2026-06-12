---
title: "Lost Top and Bottom Panels"
date: 2005-03-11
forum: Desktop Environments
---

### Post by mhykhh on 2005-03-11
Hey Guys,

I don't really know what happened but I was trying to create a new launher for nautilus by typing "sudo nautilus applications:///Internet". It opened up a window then I clicked "File->Create Launcher". It doesn't respond, I tried 4 or 5 more times but nothing happened. So I decided to reboot my PC and when I logged in, all the panels (top and bottom panels) were gone. I right-clicked my mouse, but there was no entry for "Add Panel", instead, there is an entry for "Create Launcher" as if I'm working inside a Nautilus Window. What happened and how can I fix this? Thanks

---

### Post by Xian on 2005-03-11
[QUOTE=mhykhh]I right-clicked my mouse, but there was no entry for "Add Panel", instead, there is an entry for "Create Launcher" as if I'm working inside a Nautilus Window. What happened and how can I fix this? Thanks[/QUOTE]
Just a guess....try right-clicking on your desktop > Open Terminal.
Then at the prompt type:

$ gnome-panel

---

### Post by mhykhh on 2005-03-11
[QUOTE=Xian]Just a guess....try right-clicking on your desktop > Open Terminal.
Then at the prompt type:

$ gnome-panel[/QUOTE]

I got this error

> mhyk@SERVER:/ $ gnome-panel
bash: gnome-panel: command not found

?

---

### Post by mhykhh on 2005-03-12
**Solved**

I accidentally uninstalled gnome-panel when trying to upgrade evolution mail

---

