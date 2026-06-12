---
title: "[SOLVED] eee  pc help"
date: 2008-12-07
forum: General Help
---

### Post by stan879 on 2008-12-07
hi this will be the first time using another os than c/win. 
before i install unbuntu im looking for all the drivers
for my eeepc1000H can any one help _please_

---

### Post by druellan on 2008-12-07
Hi Stan. I have Intrepid running on my eee 1000H and it rocks! My first installation was with Hardy Heron and worked better out-of-the-box, so, I recommend Hardy over Intrepid, but both work just fine.

I understand that you have Ubuntu already installed on your eee, but just in case there precofigured distros:
- Ubuntu eee here: [http://www.ubuntu-eee.com](http://www.ubuntu-eee.com)
- eeebuntu here: [http://www.eeebuntu.org/](http://www.eeebuntu.org/)

Thouse distros already have Adam's kernel wich is the best option to use on Ubuntu. If you want to add this kernel to the vanilla Ubuntu (Intrepid or Hardy) just follow the instructions here [http://www.array.org/ubuntu/setup.html](http://www.array.org/ubuntu/setup.html)

After booting with the kernel, everything should work except perhaps some function keys. To solve that, I recommend to install this set of scripts here [http://forum.eeeuser.com/viewtopic.php?id=39341](http://forum.eeeuser.com/viewtopic.php?id=39341) or here [http://forum.eeeuser.com/viewtopic.php?pid=420248](http://forum.eeeuser.com/viewtopic.php?pid=420248).

Instead of the scripts I'm currently use Greg's eee-control that is a daemon based eee control center. If you followed Adam's instruction to add his repository from array.org, you can install the control center just opening a terminal and typing:

```
sudo aptitude install eee-control
```

Just be aware that the performance controls will be disabled on the 1000H (Greg is working on that), but all the hotkeys, fan and temperature control should work ok.

Good luck!

---

### Post by druellan on 2008-12-07
Just found this thread: [http://ubuntuforums.org/showthread.php?t=963259](http://ubuntuforums.org/showthread.php?t=963259) :p

---

### Post by stan879 on 2008-12-07
thanks guys for all ur help^

---

