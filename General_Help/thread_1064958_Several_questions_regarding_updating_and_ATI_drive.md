---
title: "Several questions regarding updating and ATI drivers"
date: 2009-02-09
forum: General Help
---

### Post by Shakedown on 2009-02-09
So I'm on 8.04 and I'm looking to make some upgrades.  I'm having trouble with 3D rendering on my ATI card and I found the new ATI proprietary driver, which I want to install.  I have 2 monitors and it took me too long to get them working by messing with xorg.conf files and whatnot, so I wanted to be sure that if I get the new driver I will be able to support both monitors (from the release notes it appears I will be able to).  

I'm also considering upgrading to 8.10 to perhaps fix some other odd problems I have.

So the ATI driver says I need these packages:

"X.Org 6.7, 6.8, 6.9, 7.0, 7.1, 7.2, 7.3, or 7.4"

 - A "Xorg -version" returns X.Org X Server 1.4.0.90! Why do I have such an old version, I just bought this computer from Dell a few months ago! How do I get the latest version that supports dual monitors, and would it be better to upgrade to 8.10 for this fix?

"The display driver requires POSIX shared memory to be enabled on the system." 

 - How can I tell if I've got this?

"glibc version 2.2 or 2.3"

 - How can I tell if I've got this?

"Linux kernel 2.6 or higher"

 - Surely I have this, right?

"XFree86-Mesa-libGL"
"libstdc++"
"libgcc"
"XFree86-libs"
"fontconfig"
"freetype"
"zlib"
"gcc"

 - How can I tell if I have these?

Seeing all these requirements, would it be easier to upgrade to 8.10 before installing the new ATI driver?

Also, if I do install the new ATI driver and I have more problems that I currently do, how can I restore or re-install my current driver again?

And I don't want to do any of this if I can't have dual-monitors enabled!!

Thanks for the help

---

### Post by jbrown96 on 2009-02-09
Unless you have really, really mucked about with your system you have all of those. I'm not completely sure what X.org represents, but you have either 7.3 or 7.4 (I can't remember for Hardy). The 1.4... number is the X-server, which is different than X.org. The newest version of X-server (not in an Ubuntu release yet) is 1.6...RC, so you're not really out-of-date. I seriously doubt there have been regressions with dual-monitor support, so you should be fine to upgrade. I've found that ATI drivers are pretty good about being changed. You can install 9.1 (current) and if it doesn't work, you should be fine to switch back. I've installed about 8 different drivers on my HTPC with no problems. With NVIDIA, I can't seem to every change successfully. Just backup your xorg.conf and any of Catalyst configuration files.

---

