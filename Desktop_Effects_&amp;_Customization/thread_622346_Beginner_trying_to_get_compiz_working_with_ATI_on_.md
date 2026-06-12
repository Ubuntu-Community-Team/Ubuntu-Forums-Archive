---
title: "Beginner trying to get compiz working with ATI on Gusty Ubuntu"
date: 2007-11-24
forum: Desktop Effects &amp; Customization
---

### Post by f3rodieman on 2007-11-24
Hello all, I recently reinstalled Ubuntu 7.10 on a custom built desktop that used to run windows.  The computer as listed above has an ATI Radeon 9600pro and I can't get Compiz to run on here.  Desktop effects are enabled under visual effects, but when I try and enable compiz through terminal, it won't enable.  As the title also so I am a beginner and i know you need certain information pertaining to what comes up in terminal and potential other system specs.  Please let me know what information you require to help me diagnose this problem.  I appreciate any help.

Thanks a lot

---

### Post by Saint Angeles on 2007-11-24
ok type: ```
glxinfo | grep direct
```

---

### Post by Forlong on 2007-11-25
> **f3rodieman said:**
> Desktop effects are enabled under visual effects
Visual/desktop effects *are* Compiz. So if it's enabled, you're already running Compiz. :)

---

### Post by Saint Angeles on 2007-11-28
well the code i typed above will tell you whether or not your ATI driver is working correctly. if it outputs: no, then something is wrong.

i recommend going to [www.ati.com](www.ati.com) and d-loading the newest driver for your card. save the .run file on your desktop then open a terminal and open it with :```
sudo sh ati...
``` Instead of "..." though, hit tab to autocomplete the filename.
then once the proprietary fglrx driver is installed, run ```
aticonfig --initial
``` to configure your xorg properly.

hope this helps

---

