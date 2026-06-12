---
title: "[SOLVED] Ibus error"
date: 2013-04-29
forum: Desktop Environments
---

### Post by ibrahim52 on 2013-04-29
Since I have installed the fresh copy of ubuntu 13.04, following error appears in terminal on almost every application I try to open as "sudo".

(gedit:3423): IBUS-WARNING **: The owner of /home/xyz/.config/ibus/bus is not root!

---

### Post by ibjsb4 on 2013-04-29
Looks like a bug

[https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/1125944](https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/1125944)

---

### Post by ibrahim52 on 2013-04-29
Did the voting over there, lets see if it helps out.

---

### Post by ibrahim52 on 2013-04-30
well for those who are still facing this issue. Please follow the link below or simply go to " /home/username/.config/ibus/bus" and delete the "ibus" folder. Press CTRL+H to show hidden files on HOME to view .config folder. THANK YOU for the user who had suggested the solution through the link below.

```
https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/1125944
```

---

