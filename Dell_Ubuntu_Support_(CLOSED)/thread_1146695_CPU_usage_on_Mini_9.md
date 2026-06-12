---
title: "CPU usage on Mini 9"
date: 2009-05-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Cowchip7 on 2009-05-02
I ran Top from the terminal today while watching a video on Hulu and found my CPU running over 100%! How is the possible?

I am running Dell's lpia 8.04.

Thanks in advance for your help! :P

---

### Post by Cowchip7 on 2009-05-02
Also, I ran system monitor and found 2 file systems: /dev/sda2 and gvsf-fuse-daemon. There is also a CPU1 and CPU2 running under resources, This could explain why I can get over 100%. But why would the system be set up like that?

---

### Post by Cowchip7 on 2009-05-02
Hyperthreading answers my two CPU question. But what about the two file systems?

---

### Post by anjilslaire on 2009-05-03
/dev/sda2 is your root file system,
gvfs-fuse-daemon is a virtual userspace filesystem used by gnome, and is harmless. This is not what's causing the CPU load.

---

