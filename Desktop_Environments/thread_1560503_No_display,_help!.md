---
title: "No display, help!"
date: 2010-08-24
forum: Desktop Environments
---

### Post by spacegravity4me on 2010-08-24
So here's the deal. I finally got my wireless working and I downloaded the proprietary nvidia drivers. They installed and then the computer restarted. Upon restart I can see absolutely nothing! The monitor just says it's going to sleep. I removed the graphics card I was using and rebooted thinking that the computer would then be forced to use the graphics card on the motherboard. That didn't happen and now I don't know what to do. I thought about trying to boot from the cd but I can't get the cd drives to open. I'm up a creek here so if anybody knows anything please help me asap! Thanks

---

### Post by tad1073 on 2010-08-24
boot into recovery then select low-graphics mode, uninstall nvidia driver

---

### Post by spacegravity4me on 2010-08-25
> **tad1073 said:**
> boot into recovery then select low-graphics mode, uninstall nvidia driver

How do I boot into recovery? I'm not even seeing bios btw.:(

---

### Post by tad1073 on 2010-08-25
there should be a selection in your grub menu

---

### Post by dargaud on 2010-08-25
If you don't even see the BIOS, try holding Del, F1, F2 or F12 during boot and see if you get the BIOS (maybe it has some 'fast' option on). Check the available graphic options.

If you get psat the BIOS, try holding Shift to see if you can get in Grub.

Once in grub, edit the boot line with graphics related options like nomodeset.

If you can see neither BIOS nor Grub, then the problem is unrelated to the NVIDIA driver and some incompatibility between graphic card, cable and monitor (I have this problem: the graphic card embedded on my mobo doesn't work at all with my large cheap monitor but works with others; an old PCIx card works fine with that monitor).

---

### Post by spacegravity4me on 2010-08-25
well folks, the answer to this one is simple. Next time you take the ram out of you computer make sure you plug it back in nice and tight! LOL. Go me! Consider this problem solved.

---

