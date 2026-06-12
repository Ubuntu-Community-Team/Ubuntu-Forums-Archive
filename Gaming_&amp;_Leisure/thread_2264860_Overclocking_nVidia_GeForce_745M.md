---
title: "Overclocking nVidia GeForce 745M"
date: 2015-02-10
forum: Gaming &amp; Leisure
---

### Post by justananomaly on 2015-02-10
Note: Yes, it's a laptop. I have physical cooling mods in palce, so cooling is not so much of an issue. 

My laptop BIOS is however locked down so I can not adjust voltages, and I can overclock to +120/+240 with no issues, but I am afraid to go any higher than that without testing. Is there any preferred GPU only stress testing I can do that would help me determine my max stable?

---

### Post by R33D3M33R on 2015-02-11
Try [Furmark]("http://www.geeks3d.com/20130719/furmark-1-11-0-gpu-vga-videocard-burn-in-stress-test-opengl-benchmark-utility-nvidia-geforce-amd-radeon/") (its located in GPUtest).

---

### Post by efflandt on 2015-02-12
You can use [https://unigine.com/products/valley/](https://unigine.com/products/valley/)

You can enable a display in upper right that shows fps, gpu or gpu clock speed(?), mem speed, gpu temperature, and you can run benchmarks to test various video quality settings.

Are you using an nvidia driver 337 or newer (xorg-edgers ppa) and Option "Coolbits" "8" in xorg.conf (for gpu and mem OC offsets, or "12" for option to also control fan speed in NVIDIA X Server Settings). Although, I have not tried that with a laptop yet (will have mSATA drive next week to do fresh 14.04 install, it currently has 13.10 on hard drive partition).

---

