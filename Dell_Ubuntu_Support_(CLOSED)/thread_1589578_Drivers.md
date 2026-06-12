---
title: "Drivers"
date: 2010-10-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by BKbroila on 2010-10-06
Where do I go to get drivers? I don't have Ubuntu yet, but I will make the switch if there are stable drivers for my Dell Studio. I'm pretty sure there should be, as it's a pretty popular model. Anyways, here's my specs:

OS Version: Microsoft Windows 7 Home Premium , 64 bit
Processor: Intel(R) Core(TM)2 Duo CPU     P8600  @ 2.40GHz, Intel64 Family 6 Model 23 Stepping 10
Processor Count: 2
RAM: 4090 Mb
Graphics Card: ATI Mobility Radeon HD 4570, 256 Mb
Hard Drives: C: Total - 290203 MB, Free - 113432 MB; D: Total - 14999 MB, Free - 8021 MB; 
Motherboard: Dell Inc., 0J276M, A06, .G0TN7K1.CN4864397V0231.
Antivirus: AntiVir Desktop, Updated and Enabled

---

### Post by sanderd17 on 2010-10-06
Well, the most common drivers are build in the kernel. So they are present when you start installing ubuntu.

If you doubt, try the live CD, if it works, the installation will work too. 

There are some drivers that aren't in the kernel because they are proprietary. If ubuntu recognizes a hardware piece that needs such a driver, ubuntu will warn you and ask you to install it.

---

### Post by gordintoronto on 2010-10-06
All the hardware you described should work out of the box. What network hardware? How about printers? Webcam? Anything else?

As Sanderd mentioned, Linux takes a completely different approach to drivers than Windows. In a very real sense, everything you know about drivers can only cause you grief. Let Linux take the lead, and at some point down the road run System/Administration/Additional Drivers.

I suggest the release candidate of Ubuntu 10.10 if you are installing today.

---

