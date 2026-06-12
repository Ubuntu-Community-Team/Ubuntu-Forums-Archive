---
title: "[SOLVED] Tell my laptop it has a mic please"
date: 2008-10-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bolex100 on 2008-10-11
Dell inspiron 1525 laptop
8.04
Kernel 2.6.24.19

Lesson #1 When you get a brand new machine, make a back-up disk FIRST!!!

I needed to reinstall the o/s after 2 weeks and the included software doesn't put it all back.

I'm trying to make the wireless light work (another thread), but also, I don't think it even knows it has a built in mic.  How do I switch it on?  There is a Dell bug fix that says to switch all the "input"s to "front mic" but that does not work.

---

### Post by bolex100 on 2008-10-11
Open Volume comtrol, Edit/preferences
Check "capture" and "digtal input source".

Go into the ALSA mixer /options and change the Digital input source to "analogue inputs".  Change the Input source to "mic".

Oh yeah...... turn the faders down first!!!!!

---

