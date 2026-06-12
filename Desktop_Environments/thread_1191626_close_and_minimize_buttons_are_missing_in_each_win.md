---
title: "close and minimize buttons are missing in each window due to my numbness!!1"
date: 2009-06-19
forum: Desktop Environments
---

### Post by icivilion on 2009-06-19
hi i tried to install compiz on my friends HP AMD 64 bit laptop ..  i followed instruction from websource and i was not able to do it completely... it was for older version of ubuntu... but i am using 9.04... now i am not able to install compiz again and whatever window i open there is no close,minimize button or maxmize button and if  press show desktop icon on my desktop it says "Your window manager does not support the show desktop button, or you are not running a window manager."
 and i tried installing compiz through synaptic and when i tried i got this error...

libcompizconfig0:

Package libcompizconfig0 has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list

please help me step by step because we two are bit new to linux environment.... thanks in advance...

---

### Post by gettinoriginal on 2009-06-21
Your missing title bar can be fixed by hitting F11 twice, but also check your window "view" and be sure "full screen" is not checked.   As to the compiz problem, you should not have had to install it, as it is default in ubuntu 9.04.  Since your computer is telling you that you do not have window manager, open a terminal ( Applications > Accessories > Terminal ) and type ```
compiz --replace
```.  Welcome to Ubuntu  :P

The screenshot shows the compiz installation as installed by default.
[ATTACH]118473[/ATTACH]

---

### Post by icivilion on 2009-06-25
Thank you very much it helped a lot....:)....thanks again and lot

---

