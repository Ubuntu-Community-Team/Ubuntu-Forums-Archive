---
title: "[SOLVED] A website has corrupted my Firefox window"
date: 2009-01-01
forum: General Help
---

### Post by hotweiss on 2009-01-01
I got strange pop-up when visiting a website that maximized my Firefox so much that the top window border has disappeared (I have no upper panel) and the bottom panel to. Now when ever I start-up Firefox my window is in this super-maximized state. To get my normal window back I have to click F11 twice. Any solution?

---

### Post by gettinoriginal on 2009-01-01
I have not had to try this, but have ready quite a few threads that say if you hit F11 twice, then minimize window and change it to a smaller size, then maximize, it works.

---

### Post by hotweiss on 2009-01-01
> **gettinoriginal said:**
> I have not had to try this, but have ready quite a few threads that say if you hit F11 twice, then minimize window and change it to a smaller size, then maximize, it works.

Thanks that worked. I'm just surprised that the window size did not save after pressing F11 twice.

---

### Post by Ender41 on 2009-01-01
> **hotweiss said:**
> Thanks that worked. I'm just surprised that the window size did not save after pressing F11 twice.


 If you go to preferences, content, and then go to java-script and turn off the allow websites to change windows sizes, or however it is worded in your version that may stop it happening again.

---

### Post by gettinoriginal on 2009-01-01
Just for information, F11 only gives Full Screen or not Full Screen, it does not have anything to do with permanent settings, so cannot save anything.

---

### Post by hotweiss on 2009-01-01
> **Ender41 said:**
> If you go to preferences, content, and then go to java-script and turn off the allow websites to change windows sizes, or however it is worded in your version that may stop it happening again.

Thanks. I had no idea that this option existed.

---

### Post by caro on 2009-01-01
> **gettinoriginal said:**
> I have not had to try this, but have ready quite a few threads that say if you hit F11 twice, then minimize window and change it to a smaller size, then maximize, it works.

Sometimes when you launch FF again it will return to the maximized (blocking the upper panel) size.  If it does, hit F11 twice then resize the window making it smaller and then hit maximize button in the upper right corner.  Exit and relaunch.  Should save the setting.

---

### Post by x22 on 2009-01-02
by editing lines 13 (width) and 14 (height) of "<home_directory>.mozilla/firefox/864oeexk.default/localstore.rdf"
to read "1280" and "1024" respectively--my monitor's resolution--the size came out just right. 

You probably won't have "864...default" but "something_else.default"

---

