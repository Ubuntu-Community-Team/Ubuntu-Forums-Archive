---
title: "After rebuilding boot.ini grub does't show up"
date: 2009-02-27
forum: General Help
---

### Post by omaralqady on 2009-02-27
I had a problem with my windows system and I rebuilt boot.ini, after rebooting grub didn't show up as usual and it went straight to the windows boot menu, how can I get the grub menu back?

---

### Post by caljohnsmith on 2009-02-27
How about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
sudo grub
grub> find /boot/grub/stage1
```
The command above should return your main Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd0,2), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Reboot, and let me know if you get the Grub menu or not. We can work from there if necessary.

---

### Post by omaralqady on 2009-02-27
This worked :D Thanks a lot :D I can now boot into Ubuntu again and I am not even going to try booting into windows, I'll just format its partition :S 

Thanks again :D

---

### Post by omaralqady on 2009-02-27
I can't mark the thread as solved ! Any ideas?

---

