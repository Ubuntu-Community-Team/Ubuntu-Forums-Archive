---
title: "graphics very sluggish after unplugging from power"
date: 2017-12-07
forum: Desktop Environments
---

### Post by david-k-lam1 on 2017-12-07
I'm on 16.04, and this occurs for me with both the opensource driver, and the nvidia 384.90 driver.  It happened to me on 14.04 too.

The video card model is a GeForce GTX 850M, and I'm using the driver from the nvidia-384 package following this page:  [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

I'm using this 'glxgears' program to test video performance.

When good, it shows 10,000+ FPS
> 
      61373 frames in 5.0 seconds = 12274.539 FPS

When bad, which happens immediately after i unplug my laptop, it shows a sub 100 FPS!

      > 371 frames in 5.0 seconds = 74.048 FPS

Replugging into the A/C power does not fix the issue.  It stays at < 100 FPS.

Anyone got any ideas on how to debug it?

---

### Post by Autodave on 2017-12-07
Where did you get the Nvidia driver from?  What video card model do you have?

---

### Post by david-k-lam1 on 2017-12-07
I got the driver by installing the nvidia-384 package following this page:  [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

It's model is a GeForce GTX 850M

---

