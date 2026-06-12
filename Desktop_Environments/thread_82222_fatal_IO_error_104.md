---
title: "fatal IO error 104 ??"
date: 2005-10-26
forum: Desktop Environments
---

### Post by yhcheong on 2005-10-26
hi, I need help... I can load the GNOME. I got this error. It appeared as below on the screen. 

X10 : fatal IO error 104 (connetion reset by peer) on X server ":0.0" after 0 requests (0 known processed) with 0
events remaining.    :confused:

---

### Post by mykey on 2005-10-26
first make sure your Xserver is configured properly **sudo dpkg-reconfigure xserver-xorg** and answer the questions 
then configure gdm using **sudo dpkg-reconfigure gdm** if it does not come up by itself

---

### Post by FlashPratt on 2008-06-15
Solved my problem too; thanks yhcheong!

---

