---
title: "Problem with Deer hunter 2014 (FB game) on Ubuntu 14.04"
date: 2014-10-28
forum: Gaming &amp; Leisure
---

### Post by mirec2 on 2014-10-28
Hi everybody

Hope this is correct forum for this problem. I like to play the facebook game Deer hunter 2014. Have installed flash, and the Unity web player. This game worked great before. I haven't played it about a week or two. After game start up, it seems to be good. Everything works, but only in the small window. If I press the fullscreen button the game will crash and look weird. I also play other facebook game Ballistic, it works good. Some idea what it could be?

Thanks

---

### Post by dannyboy79 on 2014-10-28
First thing we check is what graphics card and what driver you are using. Run this in a terminal and paste the output back in this thread
```
sudo lshw -C display
```

---

### Post by mirec2 on 2014-10-28
Ok here it is.

```
 
*-display               
       description: VGA compatible controller
       product: GT200b [GeForce GTX 285]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:18 memory:fd000000-fdffffff memory:d0000000-dfffffff memory:fa000000-fbffffff ioport:9800(size=128) memory:fe680000-fe6fffff
```

---

### Post by dannyboy79 on 2014-10-29
hmmm, it appears you're already using the nvidia driver. which version do you know? did you use the restricted drivers thing in ubuntu?

---

### Post by mirec2 on 2014-10-29
I installed ubuntu about a year ago. Since the installation I do nothing with the graphics drivers.

---

### Post by dannyboy79 on 2014-10-29
i would suggest trying a different version of the nvidia driver

---

### Post by mirec2 on 2014-10-30
Ok, Do you know where I can find it? Im once tried driver from the offical nvidia page, and my computer will not boot. One of their site I don't plan to try again.

---

