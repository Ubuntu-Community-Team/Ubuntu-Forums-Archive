---
title: "[SOLVED] Compiz + Advance Desktop Effect Settings + GeForce 7950GT"
date: 2008-02-15
forum: Desktop Effects &amp; Customization
---

### Post by philidox on 2008-02-15
Everytime I start my Advance Desktop Effect Setting(ADES), Ubuntu starts acting wierd.  For example the borders on all my windows dissappear(i have to use my keyboard to minimize, maximuz, and close my programs) along with my mouse cursor.  I have Ubuntu installed on both my laptop and desktop and it only does this on my desktop.  I'm pretty sure its my configuration setting and not the vid card itself cause it works just fine.  Please help me get ADES working properly!

---

### Post by jimbob on 2008-02-15
This command has worked for some people to restore window borders (but not me).

Open a terminal window and enter:  sudo gtk-window-decorator  --replace

If that fails do a search on the word "borders" and see what comes up.  It may be a setting in your CSM that is not right.

---

### Post by philidox on 2008-02-18
Nope didnt work.  I dont think it has to do with the borders itself, remember this only happens when I start ADES.  Anyone else?

---

### Post by jimbob on 2008-02-18
In ADES, under Effects, do you have Window Decoration checked?

---

### Post by philidox on 2008-02-25
All it took was a new clean installation of ubuntu.  I had been doing upgrades from fiesty to gutsy which probably screws something up.  Nothing beats a clean installation of the latest operating system.  I'll make sure to clean install of the newest version of ubuntu as opposed to just upgrading.  Lesson learned

---

