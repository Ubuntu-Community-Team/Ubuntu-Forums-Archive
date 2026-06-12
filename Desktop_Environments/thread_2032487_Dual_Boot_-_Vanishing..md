---
title: "Dual Boot - Vanishing."
date: 2012-07-24
forum: Desktop Environments
---

### Post by jshomelinux on 2012-07-24
My PC is Dual Boot with Windows XP and Ubuntu 10.04. It works ok.

When I am upgrading or installing Ubuntu 11.10 or 12.04 the dual boot vanishes from Grub Menu. Also during the migration the process does not show presence of windows XP for importing account details. 

Regards,
JS

---

### Post by satish_j on 2012-07-24
```

sudo update-grub

```
Always try this command from ubuntu whenever you see missing OS from grub menu

---

### Post by jshomelinux on 2012-07-25
Problem unresolved after Grub update 

PC: AMD 64 with LG LCD monitor.

After booting instead of grub menu following line is displayed for 10 secs.
"Out of Range 92.5 KHz / 58 Hz"

Please help.

---

### Post by efflandt on 2012-07-25
What video card do you have?  What type of cable connects to your display?  And what resolution or model is the LG?

Does Windows XP show up in /boot/grub/grub.cfg, in which case you just have to figure out what to put in /etc/default/grub to have the grub menu display?

---

### Post by jshomelinux on 2012-07-26
Solved

[http://ubuntuforums.org/showthread.php?t=1813899](http://ubuntuforums.org/showthread.php?t=1813899)

---

### Post by claracc on 2012-07-26
> Solved

[http://ubuntuforums.org/showthread.php?t=1813899](http://ubuntuforums.org/showthread.php?t=1813899)

Please, mark the thread as solved with the "thread tools" in the upper right part of the page.

---

