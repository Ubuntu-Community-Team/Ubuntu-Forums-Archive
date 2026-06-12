---
title: "Latitude E7240 and EPort Replicator"
date: 2014-03-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Justin_Watkins on 2014-03-27
Hello,
I'm having trouble getting my dual monitors to work on a Latitude E7240 and an Eport replicator on Ubuntu 12.04. The two montiors and identical Acer V195WL, one connected VGA and the other DVI to the port replicator. When I open the Display Settings GUI it only shows one Acer montior and my laptop. I've unchecked Mirror Displays and it works between one Acer and the laptop but with both Acers plugged in it only shows one in the gui. The strange part is the image shows up on both Acers but only mirrored, I can't get it to show me all three displays (laptop, Acer1, Acer2) in the display settings. I just moved from a Toshiba Portege R700 on a docking station with the same two monitors and it worked just fine, all three displays could be used as non-mirrored. 

I've tried the latest Intel Linux Drivers which installed but didn't seem to help. 

Also Dell has a download for this model for Ubuntu 12.04 for chipset drivers, the one that caught my attention was intel-i915-backport-3.8-dkms_3.8.6.0_all.deb but I couldn't get that to install. It gave the errors
 /var/lib/dkms/intel-i915-backport-3.8-dkms/3.8.6.0/build/i915_drv.h:760:21: error: field ‘stolen’ has incomplete type
/var/lib/dkms/intel-i915-backport-3.8-dkms/3.8.6.0/build/i915_drv.h:762:21: error: field ‘gtt_space’ has incomplete type

---

### Post by michele7 on 2014-04-24
Hello Justin, any update on this topic? I have the exact same problem and I tried several things. The problem persists also on Ubuntu 14.04

Michele

---

