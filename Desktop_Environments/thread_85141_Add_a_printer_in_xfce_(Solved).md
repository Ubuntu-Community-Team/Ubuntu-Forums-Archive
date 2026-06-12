---
title: "Add a printer in xfce (Solved)"
date: 2005-11-01
forum: Desktop Environments
---

### Post by eyebrowman92 on 2005-11-01
how would i go about adding a printer for xfce? please help!

---

### Post by eyebrowman92 on 2005-11-01
Please Someone Help Me! I Need To Know How To Add A Printer In Xfce Please!!

---

### Post by aysiu on 2005-11-01
[QUOTE=eyebrowman92]how would i go about adding a printer for xfce? please help![/QUOTE] Did you start off with Gnome or KDE? The printer I added in KDE works just fine in XFCE.

---

### Post by eyebrowman92 on 2005-11-01
nvm i figured it out. i couldnt add one in xfce so i switched to gnome and added it. thanks anyway.

---

### Post by ecobuntu on 2005-11-01
localhost:631

or if you have gnome installed

gnome-cups-manager

---

### Post by eyebrowman92 on 2005-11-10
ive added a printer but it wont print no matter what. i checked everything was hooked up ok and it just refuses to print. does anyone know the problem?

---

### Post by kperkins on 2005-11-10
Can you print from Gnome?
What brand, make, and how is it hooked up to your computer etc.?

---

### Post by eyebrowman92 on 2005-11-13
i cant print from gnome. my printer is an espon stylus-photo r200. i hooked it up by going to system>administration>printing>add printer>i chose parallel port 1 (ESPON)>selected my printer>hit apply> and done. but nothing will print. what did i do wrong?

---

### Post by kperkins on 2005-11-13
Isn't the r200 connected via USB?

---

### Post by Statik on 2006-01-05
I successfully used the information in this thread: [http://ubuntuforums.org/showthread.php?t=28792](http://ubuntuforums.org/showthread.php?t=28792) to enable the CUPS web admin section. Then, going to [http://localhost:631](http://localhost:631) I was able to add my printer which is on my network through a GNet printserver. Worked great. I used the information in that thread to un-enable the CUPS web admin again, for security reasons.

Statik

---

### Post by tim15856 on 2006-01-05
The R200 is a USB only printer. Try using auto-detect to add the printer.

---

