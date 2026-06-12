---
title: "New user dealing with cryptic error"
date: 2009-03-15
forum: General Help
---

### Post by Pyth151 on 2009-03-15
Hi,

I installed Ubuntu, my first linux platform, as a dual boot with Windows XP Pro yesterday. The install and everything seemed to go fine, and I get the option to boot into either OS just fine upon start up. 

However, after selecting Ubuntu to start up, I get a brief countdown in which I can press Esc to start the Os in various states, just leaving it defaulting to normal startup, then the problem hits.

I recieve the error "[    0.004000] Aperture beyond 4gb. Ignoring."

And there it hangs. I can't even get it past this error just trying it off the boot CD.

The very little documentation I was able to locate on this error suggested it might have something to do with my mainboard lacking an AGP port. But it was poorly written and didn't offer any solutions.

My mainboard's Belarc info comes out as-

"Board: RD580-SB600 
Bus Clock: 200 megahertz
BIOS: Phoenix Technologies, LTD 6.00 PG 04/05/200"

It's a Sapphire Crossfire motherboard, the exact model # escapes me atm.

If anyone knows a work-around or fix for this problem I'd greatly appreciate it. I was rather excited to finally be ditching Windows and it's spyware/viruses.

Thanks!

---

### Post by FluffyElmo on 2009-03-15
Found a message (link below) that seems to address your problem. Add* iommu=noaperture* to the boot options and choose *basic display* when installing. Once installed you'll have to look at installing the proprietary ATI drivers to get decent performance, but hopefully this will get you going?

[http://osdir.com/ml/kubuntu-users/2009-03/msg00060.html](http://osdir.com/ml/kubuntu-users/2009-03/msg00060.html)

---

### Post by Pyth151 on 2009-03-15
Would that be drivers for my mainboard, or drivers for my video card?

I'm running an Nvidia card on an ATI board, as odd as that sounds.

---

### Post by FluffyElmo on 2009-03-15
I'm not sure, I assumed you were using integrated graphics, but probably both. If you search the forum with the name of your chipset you may find you have to install packages from ATI. I know I've seen problems with ATI chipsets mentioned in the past. The restricted driver manager should install drivers for your Nvidia card automatically. 

If you have integrated graphics you may want to make sure they are disabled in the BIOS, it may be trying to configure crossfire or something that obviously wouldn't be supported.

---

### Post by FluffyElmo on 2009-03-15
There is a bug that sounds like your problem. It has been solved in the latest 9.04 development release. You may want to download it and try it, the full release isn't due for another month so there may be bugs but it should be fairly stable. [http://www.ubuntu.com/testing/jaunty/alpha6](http://www.ubuntu.com/testing/jaunty/alpha6)

You may want to look at the bug report if you want to stick with 8.10. Some people have got it working, for instance one user had success disabling "USB BIOS Support" in the BIOS. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271070](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271070)

---

