---
title: "xorg update broke my xorg"
date: 2006-08-23
forum: Desktop Environments
---

### Post by zapcojake on 2006-08-23
Hello, I installed an update today that I believe called xorg-core-something, I don't remember for sure, now my xorg crashes on startup.  I switched to the vesa driver, tried sudo dpkg-reconfigure xserver-xorg and even copied an old backup xorg.conf over but it still won't work.  Here is the log file x points to when it crashes:

---

### Post by Uncle Spellbinder on 2006-08-23
See here:

[**_The Latest Updates Break the Xserver!_**](http://ubuntuforums.org/showthread.php?t=241254)

---

### Post by zapcojake on 2006-08-23
worked great thanks

---

### Post by ryan on 2006-08-23
This should fix it


sudo apt-get update
sudo apt-get upgrade 

They must have put the right packages in the repsoitories now.

---

