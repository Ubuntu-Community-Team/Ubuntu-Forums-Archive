---
title: "[SOLVED] change (only) amaroks icon"
date: 2008-02-24
forum: Desktop Effects &amp; Customization
---

### Post by KhaaL on 2008-02-24
I've just installed the Alpha 5 of HH and installed amarok. unfortunatly, it has a very ugly and confusing icon from my previous theme. I wonder where in my home folder are the setting for the KDEs icons and themes stored?

EDIT: I forgot to say that this is about the icon in the systray

---

### Post by sethd32 on 2008-02-24
Try looking in /usr/share/app-install/icons for amarok.png

---

### Post by KhaaL on 2008-02-24
That didn't help, the icon at the folder you pointed out is "correct". I belive it's in my home folder somewhere, i just don't know where to look... 
uploading a screenshot.

---

### Post by KhaaL on 2008-02-24
found it, for some reason it kept getting the icon from a theme located in ~/.kde/share/icons
I have no idea what file that points it there though. I'll update here if i do :)

EDIT: found it! this won't change only amaroks icon, but appearently the icon theme string is located in ~/.kde/share/config/kdeglobals  under [Icons]

Long live *grep*!

---

