---
title: "24 inch monitor not recognized"
date: 2009-09-09
forum: Desktop Environments
---

### Post by RikoW on 2009-09-09
Dear all,

I just got a brandnew Samsung SyncMaster 2443BW 24 inch screen for my Dell E4200 replacing the older Samsung 940T 19 inch screen. While the old screen is perfectly well recognized by the laptop (sitting im the dock BTW), the new screen is not recognized at all. Even while booting, I don't see the text screen of grub for example.

Also, after the machine is booting, the only connected monitor is the internal LCD. 

The 24 inch screen is working fine under windows.

Any ideas?

 Thanks,

                Riko

---

### Post by akudewan on 2009-09-09
Laptops usually have a "hotkey" (Fn+something) to toggle between monitor outputs. Have you tried using this?

---

### Post by RikoW on 2009-09-09
Yes, I tried. The problem is however, the laptop doesn't even think there is another screen but the internal one connected, so how would it toggle?

- Riko

---

### Post by RikoW on 2009-09-10
Interesting! The monitor works when I connect it via the analog port, but when connecting via the digital port, Ubuntu does not see it as connected ...

Very puzzeling :confused:

Any ideas on that around?

Thanks,

           Riko

PS: Using the digital port is important, because I have a port switcher to connected 2 PCs to one set of peripherals and that thing is digital!

---

### Post by krazyd on 2009-09-10
what graphics card and driver are you using?

---

### Post by RikoW on 2009-09-10
> **krazyd said:**
> what graphics card and driver are you using?

```
(II) Module intel: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 2.6.3
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 5.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
        i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
        E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
        965GM, 965GME/GLE, G33, Q35, Q33,
        Mobile Intel® GM45 Express Chipset,
        Intel Integrated Graphics Device, G45/G43, Q45/Q43, G41

```

---

### Post by krazyd on 2009-09-10
have you tried enabling it using xrandr?

---

### Post by RikoW on 2009-09-10
> **krazyd said:**
> have you tried enabling it using xrandr?

xrandr reports the monitor as "disconnected" even though it is plugged in!
When I plug in the old screen, it shows up ...

---

### Post by tgalati4 on 2009-09-10
How much video RAM do you have?  With Intel chipsets, you sometimes have to go into BIOS and set the amount of shared RAM to increase what is available to the video card.  It's possible that video mode uses more RAM than available causing it not to load.

There are also performance issues (and regressions) with Intel chipsets and Jaunty.  Perhaps you found another one.  Try a koala disk or using the VGA cable until koala is released (which should be shortly).

---

### Post by RikoW on 2009-09-11
The BIOS reports 32 MB but I didn't see any way to increase.

Sounds like I need to settle for VGA for now and wait for the next release.

Thanks and cheers,
                Riko

---

### Post by RikoW on 2009-09-11
> **RikoW said:**
> 
Sounds like I need to settle for VGA for now and wait for the next release.



Well, looks like Koala will not provide the solution, at least the alpha-5 release also refused to see the screen connected :(

---

### Post by RikoW on 2010-01-22
Hi,

I know, that was a long time ago, but I thought I post the "solution". It was a problem with the Monitor itself. I just got a replacement (some make and model), connected it to the digital output and there it was -  all working.

Cheers,
         Riko



> **RikoW said:**
> Interesting! The monitor works when I connect it via the analog port, but when connecting via the digital port, Ubuntu does not see it as connected ...

Very puzzeling :confused:

Any ideas on that around?

Thanks,

           Riko

PS: Using the digital port is important, because I have a port switcher to connected 2 PCs to one set of peripherals and that thing is digital!

---

