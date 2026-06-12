---
title: "installing update problem"
date: 2011-12-11
forum: Desktop Environments
---

### Post by ramus313 on 2011-12-11
i decided to update my ubuntu 11.10 on my desktop, and it installed everything, then said it neede to restart, so i restarted, and it has been stuck on the restart for quite a while now. it says "checking battery state". when i do ctr alt delete it says exiting and restartng computer and it was the pinkish startup screen that says ubuntu, then it boots into that black screen again and says checking battery state

---

### Post by ilikelinuxitisthebest on 2011-12-11
this is a really common problem. so next time. please search it first. boot up your computer. when you get to that screen push CRTL+ALT+F1 to log into a terminal session then enter this code```
sudo apt-get install lightdm-gtk-greeter
```
reboot it by typing in ```
sudo reboot
``` 
that should fix it

---

