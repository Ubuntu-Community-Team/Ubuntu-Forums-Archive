---
title: "Font too big in Skype?"
date: 2008-01-25
forum: Desktop Environments
---

### Post by netron on 2008-01-25
If you have installed the latest Skype from the medibuntu repositories, or installed KDE4 (as per the instructions on the Kubuntu home page), you might notice that your Skype fonts in Gnome will now be much too large.

the solution is to 

sudo apt-get install qt4-qtconfig

then , from the terminal, type

qtconfig-qt4


set the font to something less massive,  then select File -> Save. the qtconfig fonts should now change - and skype's fonts do as well.

i hope this helps some folks out there, as this had me stumped for a while this evening.

---

### Post by K.Mandla on 2008-01-25
Moved to Desktop Environments.

---

### Post by Daniel_D on 2008-04-24
Thx that you took your time to post this!

Had the same prblm.

Ciao
Daniel

---

