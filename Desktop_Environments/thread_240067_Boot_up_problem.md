---
title: "Boot up problem"
date: 2006-08-20
forum: Desktop Environments
---

### Post by Sinne on 2006-08-20
I had WinXP and Ubuntu installed on my computer. Of course, at boot up, I could choose between these two.

Recently, I re-installed the WinXP, and now it just boots, without letting me choose between it and Ubuntu. Now, I can't use my Ubuntu. Can I fix this, without reinstalling Ubuntu? Please help.

Thank you.

---

### Post by Iarwain ben-adar on 2006-08-20
Hi,
yes you can :D

Just pop in the live cd and boot.

Then you actually just reinstall GRUB. ```
sudo grub
find /boot/grub/stage1
root (hdx,y)    (x,y being the output of the previous command)
setup (hdx)
quit
```


Iarwain

---

### Post by Sinne on 2006-08-20
I'll try this. Thank you.

Btw, is there a chance to screw up the Windows partition while doing this?

---

### Post by Iarwain ben-adar on 2006-08-20
Normally you can't screw up :D


Iarwain

---

