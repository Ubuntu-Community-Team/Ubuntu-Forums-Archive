---
title: "NVidia Temps"
date: 2005-09-10
forum: Gaming &amp; Leisure
---

### Post by idn on 2005-09-10
Is there a way to find out the temperature at which my 7800gtx is running at. I am using the official latest nvicia drivers if that haelps

---

### Post by linkunderscore on 2005-09-11
Yea..you can install the nvidia x server settings program.

---

### Post by idn on 2005-09-11
Yeah I haev that but it doesnt show the temps for it, I am using the official nvidia drivers. Would it be in a log file somewhere?

---

### Post by idn on 2005-09-17
Does anyone have any ideas on this one?

---

### Post by linkunderscore on 2005-09-17
yep :) 

sudo apt-get install nvidia-settings


you can see real-time temps

---

### Post by idn on 2005-09-17
For some reason it doesnt show my temps, I thnk it maybe a BIOS settng or something. I'll ask around on teh nvidia forums uinless anyone has any other ideas?

---

### Post by shawn on 2005-09-18
idn: i recently put 7667 nvidia drivers on my Breezy installation. Coolbits wont show and neither will the temp reading. I have tried all sorts of settings and whatnot.

This was my only help:

[http://www.linuxhardware.org/nvclock/](http://www.linuxhardware.org/nvclock/)

Its like an alternative to nvidia-settings, works ok for me.

---

### Post by idn on 2005-09-19
Ok I'll give it a try, do you have a 7800gtx?

---

### Post by shawn on 2005-09-19
No I have a 6600GT. Let me know if it works out for you.

---

### Post by gil-galad on 2005-09-19
Try nvclock, that worked for me.

---

