---
title: "Odd error I don't understand"
date: 2006-06-21
forum: Desktop Environments
---

### Post by inovermyheadd on 2006-06-21
Hey I am getting this when booting up:

17179572.3920001 PCI cannot allocate resource region 7 of bridge 0000:00:lc.1
17179572.3920001 PCI cannot allocate resource region 8 of bridge 0000:00:lc.1
17179572.3920001 PCI cannot allocate resource region 9 of bridge 0000:00:lc.1

anyone have a clue what it means?

---

### Post by David_T on 2006-06-21
If you are able to boot up successfully, can you post the output of the command lspci?  This will tell you which device 0000:00:lc.1 is.

---

### Post by inovermyheadd on 2006-06-23
0000:00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) P CI Express Port 2 (rev 04)

this is what I got for 0000:00:1c.1

should I post more of the output?

---

