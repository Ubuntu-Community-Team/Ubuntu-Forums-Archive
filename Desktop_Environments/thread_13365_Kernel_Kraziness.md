---
title: "Kernel Kraziness"
date: 2005-01-30
forum: Desktop Environments
---

### Post by bitfoo on 2005-01-30
Hello.  I recently made some changes to Warty.

1. I installed the 2.6.10 kernel from warty-backports.  Everything went perfect.
2. I then patched and recompiled this kernel according to [http://www.ubuntulinux.org/wiki/KernelHowto/](http://www.ubuntulinux.org/wiki/KernelHowto/)
Also, I did "make oldconfig," which is not mentioned in that wiki since I wanted everything that I already worked on to work just as well with the hacked kernel.

I had to patch because my battery was not being read correctly, and you can read about the patch here -> [http://m6n.ath.cx/aml_method_exec_hack.patch](http://m6n.ath.cx/aml_method_exec_hack.patch)

Anyway, the patch worked.  Great! Now I can see how much battery I have left! :)

But it also broke some stuff.  I've only noticed two things so far that are broken, but there might be more.

1. My wireless no longer works.  The card isn't even detected.  Here is the dmesg output.
```

bitfoo@horus:~ $ dmesg|grep ipw2200
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 0.19
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
ipw2200: ipw-2.2-boot.fw load failed: Reason -2
ipw2200: Unable to load firmware: 0xFFFFFFFE
ipw2200: failed to register network device
ipw2200: probe of 0000:02:02.0 failed with error -5
```

Ahh you say, the firmware is not loading. But it must be...
```

bitfoo@horus:~ $ lsmod | grep ipw2200
ipw2200                74412  0
firmware_class         10176  1 ipw2200
ieee80211              23844  1 ipw2200
```

2. This new kernel doesn't use the ATI drivers I have installed, only MESA 3D.  But if all kernels use the same XF86Config-4, it should work right? Anyway, I don't know what to paste for this problem so let me know.

It's like I take one step forward and two steps back.  :cry:  :cry:  :cry:

---

### Post by mendicant on 2005-01-30
You need to rebuild the ATI drivers for every kernel change you make.

---

### Post by bitfoo on 2005-01-30
How do you rebuild them if they are already apt-get installed  :confused:  :confused:  :confused:

Also this is what this says:

```
bitfoo@horus:~ $ cat /proc/sys/kernel/hotplug
/sbin/hotplug

```

---

### Post by bitfoo on 2005-01-30
I have been told that kernel howto is crap and should rebuild it without messing with the version.  i will post more when its done.

---

### Post by mendicant on 2005-01-30
Not sure why you posted the hotplug thing, but in any case, you can install multiple versions of the ATI driver.  It will reinstall the libGL.so, but that's okay--it's the same library for the same version of the ATI driver.  For the ATI driver, you'll have to check if you need to do anything special for a 2.6.10 kernel, but other than that, just follow the ATI directions should work (running /lib/modules/fglrx/..../<whatever the shell script is called>).  You probably have a .deb package for your old kernel.  You can keep that installed if you want (it might be wise until you have it working in 2.6.10).  But once you're happy with your new kernel, you can remove it.

I seem to recall you had to have the actual kernel sources for your kernel to build the ATI module (yet another reason not to like them--they should only need the headers), so make sure you have those still lying around.

---

### Post by bitfoo on 2005-01-31
Wow so I have to actually compile the drivers instead of installing a deb.  That blows. :( Any ideas on the wireless? Or do I have to recompile those as well. :/

---

### Post by mendicant on 2005-01-31
I've never used the Intel stuff.  You might want to repost that as a separate question.  I know that I often don't bother to look at forum posts that already have a number of replies to them.

---

