---
title: "1280*960 resolution with and intel!"
date: 2008-06-14
forum: Desktop Environments
---

### Post by slsolaris on 2008-06-14
I have an Intel 82845 G/GL/GE/PE/GV Graphics Controller and a FS7555 Compaq CRT Monitor and i would like to change my resolution to 1280*960 px, but i cant, because it dont show me the option an when i change my resolution to 1024*768 to 1280*1024 my screen goes wrong, it looks very bad! please help me, i dont know if it is about drivers, if it is that please tell me about a link i could download the drivers from.
thanx!!

---

### Post by prshah on 2008-06-14
> **slsolaris said:**
>  i would like to change my resolution to 1280*960 px, but i cant, because it dont show me the option


Can you give the following information? Press Alt+F2, then type in ```
displayconfig-gtk
``` and press enter. Dismiss the warning about "Administrator mode", then click on the "Graphics Card" tab, and tell us which graphics card driver is being used, and the amount of video memory.

---

### Post by slsolaris on 2008-06-14
845 intel

---

### Post by prshah on 2008-06-15
> **slsolaris said:**
> 845 intel

Better post a screenshot of the driver window. Is the driver "intel experimental modesetting driver"?

---

### Post by p_quarles on 2008-06-15
```
sudo apt-get install 915resolution
```
Restart the X server, and everything should be golden. If it doesn't automatically fix the resolution, it should now give you the option you want.

---

### Post by slsolaris on 2008-06-30
i'll do it, let me see!!

---

### Post by mjwhitfield on 2008-06-30
We can't see files on your desktop :)

---

