---
title: "Can not record any audio from line-in."
date: 2006-01-09
forum: Desktop Environments
---

### Post by Majiman on 2006-01-09
Hello.  I am trying to record sound from the analog line input (line-in) jack on my sound card.  I can't seem to capture anything with the Sound Recorder that comes with Ubuntu or Audacity.  Is it possible to record from the line-in in Ubuntu/Linux?  Here's a basic rundown of my system specs.

CPU: AMD Athlon XP 3000+
Sound Card: Sound Blaster Audigy 2 ZS
OS: Ubuntu 5.10 (Fully updated.)

Thanks in advance for any help or suggestions.

---

### Post by lnostdal on 2006-01-09
you might have tried this but; in the volume control, try unmuting and/or selecting line-in as "source"   (under the capture-section)

---

### Post by Majiman on 2006-01-09
Thanks for the reply Inostdal.  In volume control I've double checked and made sure that my Line-In volume is all the way up and unmuted.

However, I can not find the "capture section".  Is that in the Volume Control?

---

### Post by handy on 2006-01-09
Have you had a look at **alsamixer**?

Just type its name into the terminal, you navigate with the cursor control keys.

Cheers,

handy

---

### Post by Majiman on 2006-01-09
I finally got it working!  I had to enable **Analog Mix** as well as Line-In in order for it to work.  I can now record from my line-in jack.  Thanks for your feedback guys.  :D

---

### Post by Double A Ron on 2006-01-20
majiman, are you using an audigy 2 by chance.  I can't find the "capture section in my audigy controls.

---

### Post by girionis on 2006-02-07
Majiman I have the same problem. Where did you enable Analog Mix and Line-in from?

---

