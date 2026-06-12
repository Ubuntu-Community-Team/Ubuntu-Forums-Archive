---
title: "Not Faster on 686 Kernel?"
date: 2006-07-15
forum: Desktop Environments
---

### Post by SuperMike on 2006-07-15
I can't seem to see any difference on the Ubuntu Pentium 686 instruction set kernel version versus the 386 instruction set. Is there something I'm doing wrong?

:sad: 

I have a Dell Optiplex GX150 now with a Pentium III processor that runs about 1.1Ghz, I think. I had heard that if you want to improve the speed of Ubuntu, switch it from the default of a 386 kernel to the 686 kernel. Ubuntu wants to make their stuff work on the largest set of processor types, so they give you the 386 version by default. I just found this out.

You can upgrade by doing this:

# sudo apt-get install linux-686

Then, reboot.

Then, go into Synaptic Package Manager and search for "386". If you find anything kernel-related that is green (meaning, installed), right-click and remove it. HOWEVER, when it tries to remove, it will stop and you'll get a warning that is important. You have to click "Show Terminal" to see this warning during the removal process. Note what it says. It will tell you that you shouldn't do one set of removals, and so I DID NOT and typed "n" for No. I then rebooted and came up just fine under the 686 kernel.

Now, go back and do the Synaptic Package Manager process and reboot as many times as you can to remove any old 386 kernel residue. Click "Show Terminal" and see if it has more warnings and if it warns you something critical, type "n" for No. However, I just did this after my reboot on the 686 kernel and this time it did the removal without bugging me and all is well.

You actually don't need to do the 386 process, but if you don't, when Ubuntu gets its next round of updates, it will download both 686 AND 386 updates.

---

### Post by dtfinch on 2006-07-15
The speed difference is almost immeasurably small. It's still optimized for modern processors, but using only i386 instructions. I don't think that prevents the kernel from using MMX and such in some cases when it detects you have a newer processor though.

Their basic argument for defaulting to the i386 build is that they haven't seen a single benchmark where i686 is faster, the i386 builds are better tested, and there are some cheap processors like the Via C3 that don't even support all of the i686 instructions. The gcc output for i386 and i686 are almost identical anyways.

---

