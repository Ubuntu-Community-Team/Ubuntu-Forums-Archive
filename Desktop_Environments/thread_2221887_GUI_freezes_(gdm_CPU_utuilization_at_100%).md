---
title: "GUI freezes (gdm CPU utuilization at 100%)"
date: 2014-05-04
forum: Desktop Environments
---

### Post by rinia on 2014-05-04
I get often a GUI freeze on my eeepc 1015PN (VGA: NVIDIA Corporation GT218 [ION]). If I open a ssh shell from another computer I can see that gdm has a CPU utilization at almost 100%. If I look at the kern.log I found the following traces:


```
May  4 13:11:32 Neptun kernel: [  957.872327] nouveau E[   PFIFO][0000:04:00.0] DMA_PUSHER - ch 3 [Xorg[1051]] get 0x0020025550 put 0x002002694c ib_get 0x00000137 ib_put 0x0000014e state 0x80000030 (err: INVALID_CMD) push 0x00400040
May  4 13:11:37 Neptun kernel: [  962.558183] nouveau E[   PFIFO][0000:04:00.0] DMA_PUSHER - ch 3 [Xorg[1051]] get 0x0020027c7c put 0x00200287e0 ib_get 0x00000301 ib_put 0x0000032a state 0x8000e684 (err: INVALID_CMD) push 0x00400040
May  4 13:11:37 Neptun kernel: [  962.572833] nouveau E[  PGRAPH][0000:04:00.0] DATA_ERROR BEGIN_END_ACTIVE
May  4 13:11:37 Neptun kernel: [  962.572848] nouveau E[  PGRAPH][0000:04:00.0]  DATA_ERROR
May  4 13:11:37 Neptun kernel: [  962.572862] nouveau E[  PGRAPH][0000:04:00.0] ch 3 [0x001fb14000 Xorg[1051]] subc 7 class 0x8597 mthd 0x1360 data 0x00000001
May  4 13:11:37 Neptun kernel: [  962.572910] nouveau E[  PGRAPH][0000:04:00.0] DATA_ERROR BEGIN_END_ACTIVE
May  4 13:11:37 Neptun kernel: [  962.572933] nouveau E[  PGRAPH][0000:04:00.0]  DATA_ERROR
May  4 13:11:37 Neptun kernel: [  962.572947] nouveau E[  PGRAPH][0000:04:00.0] ch 3 [0x001fb14000 Xorg[1051]] subc 7 class 0x8597 mthd 0x1340 data 0x00008006
May  4 13:11:37 Neptun kernel: [  962.572999] nouveau E[  PGRAPH][0000:04:00.0] DATA_ERROR BEGIN_END_ACTIVE
May  4 13:11:37 Neptun kernel: [  962.573018] nouveau E[  PGRAPH][0000:04:00.0]  DATA_ERROR
May  4 13:11:37 Neptun kernel: [  962.573049] nouveau E[  PGRAPH][0000:04:00.0] ch 3 [0x001fb14000 Xorg[1051]] subc 7 class 0x8597 mthd 0x1344 data 0x00004001
May  4 13:11:37 Neptun kernel: [  962.573094] nouveau E[  PGRAPH][0000:04:00.0] DATA_ERROR BEGIN_END_ACTIVE
May  4 13:11:37 Neptun kernel: [  962.573108] nouveau E[  PGRAPH][0000:04:00.0]  DATA_ERROR
May  4 13:11:37 Neptun kernel: [  962.573122] nouveau E[  PGRAPH][0000:04:00.0] ch 3 [0x001fb14000 Xorg[1051]] subc 7 class 0x8597 mthd 0x1348 data 0x00004303
May  4 13:11:37 Neptun kernel: [  962.573169] nouveau E[  PGRAPH][0000:04:00.0] DATA_ERROR BEGIN_END_ACTIVE
May  4 13:11:37 Neptun kernel: [  962.573193] nouveau E[  PGRAPH][0000:04:00.0]  DATA_ERROR
May  4 13:11:37 Neptun kernel: [  962.573210] nouveau E[  PGRAPH][0000:04:00.0] ch 3 [0x001fb14000 Xorg[1051]] subc 7 class 0x8597 mthd 0x134c data 0x00008006
May  4 13:11:37 Neptun kernel: [  962.573258] nouveau E[  PGRAPH][0000:04:00.0] DATA_ERROR BEGIN_END_ACTIVE
May  4 13:11:37 Neptun kernel: [  962.573272] nouveau E[  PGRAPH][0000:04:00.0]  DATA_ERROR
May  4 13:11:37 Neptun kernel: [  962.573296] nouveau E[  PGRAPH][0000:04:00.0] ch 3 [0x001fb14000 Xorg[1051]] subc 7 class 0x8597 mthd 0x1350 data 0x00004001
May  4 13:11:37 Neptun kernel: [  962.573331] nouveau E[  PGRAPH][0000:04:00.0] DATA_ERROR BEGIN_END_ACTIVE
May  4 13:11:37 Neptun kernel: [  962.573344] nouveau E[  PGRAPH][0000:04:00.0]  DATA_ERROR
May  4 13:11:37 Neptun kernel: [  962.573358] nouveau E[  PGRAPH][0000:04:00.0] ch 3 [0x001fb14000 Xorg[1051]] subc 7 class 0x8597 mthd 0x1358 data 0x00004303
May  4 13:11:37 Neptun kernel: [  962.606111] nouveau E[   PFIFO][0000:04:00.0] DMA_PUSHER - ch 3 [Xorg[1051]] get 0x0020027b8c put 0x0020027c28 ib_get 0x00000357 ib_put 0x0000036a state 0x8000ef05 (err: INVALID_CMD) push 0x00400040
May  4 13:16:19 Neptun kernel: [ 1244.369029] nouveau E[   PFIFO][0000:04:00.0] DMA_PUSHER - ch 3 [Xorg[1051]] get 0x0020024ee8 put 0x0020026e54 ib_get 0x0000031b ib_put 0x0000031e state 0x80004214 (err: INVALID_CMD) push 0x00900031

```

I have also tried the lightdm with the same result (freeze). What can I do?

---

### Post by rinia on 2014-05-25
After some research I found the solution. The open-source graphics device driver *nouveau* used by the Ubuntu installation process has some problems. After installing the NVIDIA driver it works like a charm. You must [download]("http://www.nvidia.com/Download/index.aspx?lang=en-us") the driver and install it. The installation process also blacklists the old driver.

---

