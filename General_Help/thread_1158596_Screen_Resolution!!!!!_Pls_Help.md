---
title: "Screen Resolution!!!!! Pls Help"
date: 2009-05-13
forum: General Help
---

### Post by gathri on 2009-05-13
I have ubuntu9.04 installed (jaunty) under windows XP. The screen res is 800*600. My monitor supports 1024*768. But, the system>Display drop down list doesn't show the desired resolution. Please Help (Im a novice to ubuntu, especially with sudo codes)

---

### Post by gathri on 2009-05-13
I have ubuntu9.04 installed (jaunty) under windows XP. The screen res is 800*600. My monitor supports 1024*768. But, the system>Display drop down list doesn't show the desired resolution. Please Help (Im a novice to ubuntu, especially with sudo codes)

---

### Post by Tipped OuT on 2009-05-13
Hello, make sure you have all the updates installed and go to System< Administration< Hardware Drivers.

---

### Post by MurkMenthaa on 2009-05-13
> **gathri said:**
> I have ubuntu9.04 installed (jaunty) under windows XP.

Did you mean virtual machine or wubi ?
I had that problem with virtual machine (mine was ubuntu within ubuntu though), here's the solution : [http://www.linuxformat.co.uk/index.php?name=PNphpBB2&file=viewtopic&t=6438](http://www.linuxformat.co.uk/index.php?name=PNphpBB2&file=viewtopic&t=6438)

---

### Post by overdrank on 2009-05-13
Threads merged. :)

---

### Post by LarkAnjana on 2009-05-14
I have exactely same problem
system>administration>display shows max resolution as 800x600
i did most what i could but no luck
could anyone please provide step by step guide on how to enable higher resolutions.
Also when i open xorg.conf in ubuntu 9.04. following entries are there and there is no extra information:

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

---

