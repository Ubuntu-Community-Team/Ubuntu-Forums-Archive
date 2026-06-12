---
title: "ATI fglrx driver 8.18.6 Change to 16bit"
date: 2005-11-01
forum: Desktop Environments
---

### Post by Donnut on 2005-11-01
Hi! How do I change the new ATI driver to run X at 16bit?  I tried sudo dpkg-reconfigure xserver-xorg, but didn't know which driver to choose.  When I selected the "ati" driver, it brought me back to Mesa.  When I selected "fglrx" it gave me a blank, white screen.   I finaly got the old ATI driver installed by repeating the steps in the how-to.  But it doesn't solve the problem....

---

### Post by Teroedni on 2005-11-02
If i get what you mean
You want to run ati binary at 16 bit??

To do that
Open terminal
paste the command down under
sudo gedit /etc/X11/xorg.conf

Post the text file you get here

---

### Post by Donnut on 2005-11-02
Do I change where it says "depth" to 16 instead of 24?

---

### Post by drummer on 2005-11-02
[QUOTE=Donnut]Do I change where it says "depth" to 16 instead of 24?[/QUOTE]
For 16-bit colour depth? That should do it.

---

