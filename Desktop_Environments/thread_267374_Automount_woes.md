---
title: "Automount woes"
date: 2006-09-28
forum: Desktop Environments
---

### Post by smbm on 2006-09-28
I have recently compiled and installed my own kernel from kernel.org sources. I thought everything had been succesful when I rebooted and everything seemed hunky dory. However everything was far from hunky dory (possible overstatement) because automounting my flash drive or ipod no longer worked. Can anybody help me solve this problem? I have tried searching these forums but can't seem to find anything conclusive to help sort it out.

Thanks in advance.

---

### Post by aysiu on 2006-09-28
Have you tried this? ```
sudo aptitude update
sudo aptitude install gnome-volume-manager
gnome-volume-manager &
```

---

### Post by smbm on 2006-09-28
Will try it as soon as I get home. In the meantime thanks for your speedy reply.

---

### Post by smbm on 2006-09-28
Doesn't seem to have solved the problem. Anything else you can think of?

---

### Post by smbm on 2006-09-28
When I plug my ipod in device manager updates. Still no automounting though.

---

### Post by smbm on 2006-09-28
When I start my computer I get a message about being unable to create a udev queue. I'm guessing this is the cause. Did I mess something up in the kernel config? Anyone anywhere have any ideas how to fix this?

---

### Post by smbm on 2006-09-28
I guess I'll just go back to my old kernel. Oh well. Shame to be defeated.

---

