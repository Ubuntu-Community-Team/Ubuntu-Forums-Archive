---
title: "Compiz works but..."
date: 2008-01-15
forum: Desktop Effects &amp; Customization
---

### Post by xRes on 2008-01-15
Ok my graohics card is obviously blacklisted for compiz but I can get it to run by using:

> SKIP_CHECKS=yes compiz --replace

I have added it to the session manager so it hopefully would do this on start-up but it doesn't seem to be doing it as after the OS boots, the Appearance is set back to 'none' and I cant select 'extra'!

Any ideas?:confused:
Thanks
xRes

---

### Post by xRes on 2008-01-20
Bump

Any ideas or thoughts much appreciated!

---

### Post by tragicglee on 2008-01-20
hit ALT + F2, type or paste the following into the run box:  gedit ~/.config/compiz/compizconfig/config ...  You will need to add **skip_checks = yes** to the end of that's just opened. Save, and you should be good. ALT + CTRL + backspace to restart X and verify.

---

### Post by xRes on 2008-01-21
sorted thanks

---

