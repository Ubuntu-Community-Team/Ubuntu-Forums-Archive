---
title: "Wireless Driver"
date: 2011-06-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Raeray on 2011-06-05
I recently upgraded to the latest version of Ubuntu 11. For some reason, my wireless is no longer working. I have spent hours trying to figure this out. I am fairly new to ubuntu, I am lost and very frustrated; I need help and I don't know where to start. HELP!!!

---

### Post by mikewhatever on 2011-06-05
Hi, and welcome to the forum.
Hope we can help you, because if the wifi worked in another version of Ubuntu, it should also work in 11.04.
To identify your wireless card, and make sure the driver is installed, please open a terminal window and post the outputs of the following:

```
lspci -nn

lshw -C network
```

---

