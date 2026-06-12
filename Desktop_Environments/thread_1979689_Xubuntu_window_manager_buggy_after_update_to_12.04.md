---
title: "Xubuntu window manager buggy after update to 12.04"
date: 2012-05-13
forum: Desktop Environments
---

### Post by xierdudeC on 2012-05-13
After I updated to Xubuntu 12.04 Precise Pangolin my windows got messed up. First of all, they have no borders. Second, the buttons on top to close, minimize, etc. are all gone, so it is difficult to manage windows quickly. Finally, none of the open windows show up on my taskbar at the top.

Thanks a lot for your help!

---

### Post by Toz on 2012-05-13
Hello and welcome to the forums.

It sounds like your window manager has crashed. Try Alt-F2 and running:
```
xfwm4 --replace
```
...to get it restarted.

---

### Post by xierdudeC on 2012-05-14
Thanks! Worked perfectly.

---

### Post by Rodney9 on 2012-05-15
> **Toz said:**
> Hello and welcome to the forums.

It sounds like your window manager has crashed. Try Alt-F2 and running:
```
xfwm4 --replace
```
...to get it restarted.

Thank You Toz, I needed this today on my Xubuntu 12.4 64Bit after rebooting.

Rodney

---

### Post by peyre on 2013-02-17
This worked for me too!  FYI, I had to reboot for the change to take effect.

---

### Post by Ian Clark on 2013-03-09
this solution worked for me today. dunno why this keeps happening with xubuntu 12.04! but thanks for the solution. btw i didn't need to reboot.

---

