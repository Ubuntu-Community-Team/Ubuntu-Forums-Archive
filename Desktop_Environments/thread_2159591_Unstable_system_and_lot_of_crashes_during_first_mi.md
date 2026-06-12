---
title: "Unstable system and lot of crashes during first minutes after startup"
date: 2013-07-03
forum: Desktop Environments
---

### Post by gohatto on 2013-07-03
Hi guys.

Since few months I'm experiencing tremendously irritating problem in Ubuntu. System, after about** 5 - 10** minutes after startup is **very unstable**. It produces a lot of "System has experienced problem" errors (typical Gnome error windows), Thunderbird and Firefox crashes all the time, etc. Sometimes even VLC is no running properly.

After those 5 - 10 minutes, everything seems to stabilize and no crashes occurs. I have no idea where to start looking for the cause of this behavior. 
Can it be a SSD problem? 
GPU? 
Ubuntu itself?
64 bit? 
Gnome 3 / Unity?

I'm using Gnome 3 for my everyday work but I've tested it on Unity and Thunderbird and Firefox are still unstable for those first few minutes.

I would be obliged for any ideas how to investigate this problem. If you need any more details, some dumps or results of some checking - I will of course post it here. I am desperate to found a source of this problem.

I'm currently using Ubuntu 13.04 64bit but the same problem was with 12.10 64bit.

**OS**: Linux version 3.8.0-25-generic (buildd@roseapple) (gcc version 4.7.3 (Ubuntu/Linaro 4.7.3-1ubuntu1) ) #37-Ubuntu SMP Thu Jun 6 20:47:07 UTC 2013
**CPU**: Intel Core i7-3770K, 3,5Ghz
**GPU**: GeForce GTX 660 Ti
**SSD**: Corsair Neutron GTX 240GB
**SSD** Optimizations made according to: [https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)
Disk organization (SSD):
   1. partition, 700 MB (/boot/efi)
   2. partition, 42 GB (/)
   3. partition, 168 GB (/home)
   4. unused space: 14 GB

(swap partition is on HDD disk - ca. 4,5 GB)

**Gnome 3 version**: 3.8.2-1ubuntu2~raring2

Below you can find an exemplary crash report from Firefox:

-----------------------------

> Add-ons: %7BDDC359D1-844A-42a7-9AA1-88A850A938A8%7D:2.0.16,%7B8b86149f-01fb-4842-9dd8-4d7eb02fd055%7D:0.26,%7B19503e42-ca3c-4c27-b1e2-9cdb2170ee34%7D:1.5.5.5,%7B73a6fe31-595d-460b-a920-fcc0f8843232%7D:2.6.6.6,%7B6AC85730-7D0F-4de0-B3FA-21142DD85326%7D:2.8,%7B972ce4c6-7e08-4474-a285-3208198ce6fd%7D:22.0,firebug%40software.joehewitt.com:1.11.4,%7Bd10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d%7D:2.2.4,langpack-en-ZA%40firefox.mozilla.org:22.0,langpack-en-GB%40firefox.mozilla.org:22.0,langpack-pl%40firefox.mozilla.org:22.0
BuildID: 20130620122336
CrashTime: 1372883027
EMCheckCompatibility: true
FramePoisonBase: 7ffffffff0dea000
FramePoisonSize: 4096
InstallTime: 1372447985
Notes: OpenGL: NVIDIA Corporation -- GeForce GTX 660 Ti/PCIe/SSE2 -- 4.2.0 NVIDIA 304.88 -- texture_from_pixmap

ProductID: {ec8030f7-c20a-464f-9b0e-13a3a9e97384}
ProductName: Firefox
ReleaseChannel: release
SecondsSinceLastCrash: 15723
StartupTime: 1372883025
Theme: classic/1.0
Throttleable: 1
Vendor: Mozilla
Version: 22.0

This report also contains technical information about the state of the application when it crashed.

----------

Thanks in advance for any help!

Regards,
Piotr

---

### Post by claracc on 2013-07-04
I would start looking for proprietary drivers for your nvidia graphics card: [http://www.howopensource.com/2012/10/install-nvidia-geforce-driver-in-ubuntu-12-10-12-04-using-ppa/](http://www.howopensource.com/2012/10/install-nvidia-geforce-driver-in-ubuntu-12-10-12-04-using-ppa/)

---

### Post by gohatto on 2013-07-05
Thanks claracc for your advise.

I've added appropriate repo but it didn't help. I have nvidia driver in the following version:

Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: nvidia-graphics-drivers-304
Version: 304.88-0ubuntu1

Any other ideas? Proprietary drivers from nVidia site instead of these from Ubuntu repository?
Maybe it's a SSD failure? How to best check for disk errors?

Any other ideas are warmly welcome :-)

Thanks in advance!

---

### Post by slickymaster on 2013-07-05
> **gohatto said:**
> ...
Maybe it's a SSD failure? How to best check for disk errors?...

You can use SMART data reader, in System > Administration > Disk utility.

---

### Post by gohatto on 2013-07-05
S.M.A.R.T. says disk should be fine. I've run extended self-test and here you can fine the results:

[ATTACH=CONFIG]244428[/ATTACH]

What else can be checked?

---

### Post by slickymaster on 2013-07-05
Well, it won't hurt if you check your RAM. You can do it by booting with a Ubuntu LiveCD, and select **TEST MEMORY with memtest+**

---

### Post by gohatto on 2013-07-14
Thanks slickymaster,

I've run memtest for ca. 2 hours and here are the results:

[ATTACH=CONFIG]244715[/ATTACH]

So it seems that RAM is fine... what's next to check?

Thanks in advance!

---

### Post by slickymaster on 2013-07-15
As apparently there's nothing wrong with your hardware, everything points to the fact that claracc was right in the first place and the problem can be related to your graphics card. See this thread: [http://ubuntuforums.org/showthread.php?t=2142117](http://ubuntuforums.org/showthread.php?t=2142117)

---

