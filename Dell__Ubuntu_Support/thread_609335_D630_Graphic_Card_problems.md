---
title: "D630 Graphic Card problems"
date: 2007-11-10
forum: Dell  Ubuntu Support
---

### Post by ranjiao on 2007-11-10
I just followed the instruction of some posts of D630 and installed driver from nvidia NVIDIA-Linux-x86_64-1.0-9631-pkg1.run, but there's still something odd.

Every time I boot the machine the screen model turn into 800*600 again and I have to change it after login.

PS: I turned on the visual effect and I'm not sure what driver I am using now.

---

### Post by Triptol on 2007-11-15
Can't answer the 800x600 part of your post, but you can tell what driver you are using by examining your /var/log/Xorg.0.log file ```
cat /var/log/Xorg.0.log | grep Driver
``` shoudl do the trick.

---

