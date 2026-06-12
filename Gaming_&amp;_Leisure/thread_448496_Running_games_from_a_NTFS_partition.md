---
title: "Running games from a NTFS partition?"
date: 2007-05-19
forum: Gaming &amp; Leisure
---

### Post by blackjackel on 2007-05-19
Has anyone done this before?

Maybe had a game installed through windows, then rebooted in ubuntu and without running the installer got it got it to run on linux from the already installed files on NTFS?

---

### Post by ebichu on 2007-05-19
Those games, that don't depend on the registry entries should run just fine, also, I think you need write support/permission for ntfs drive too, to run them.

---

### Post by blackjackel on 2007-05-19
So ubuntu has by default read access but not write? Is it safe to enable write support for NTFS?

---

### Post by blackjackel on 2007-05-19
Also, I have no idea how to emulate windows registry keys in linux, is there a guide on how to do such a thing somewhere out there? I'm quite familiar with the windows registry and how to edit it in windows, so perhaps it wouldnt be too difficult for me to figure out...

---

### Post by ebichu on 2007-05-19
You have to export needed registry keys in windows, and in linux you have to type: wine regedit asd.reg, where asd.reg is the name of the registry file you exported.

---

