---
title: "Ivy Bridge MB unstable, hangs, and DRM failures on 12.04"
date: 2012-07-10
forum: Desktop Environments
---

### Post by PencilGeek on 2012-07-10
I just bought a brand new Asus Ivy Bridge motherboard, installed fresh 12.04 download.  About one of four boots, X won't start.  The Xorg log file complains of DRM failures.
 
When the desktop is running, the system will occasionally hard hang.  It hard hangs so bad that the RESET button won't recover it, but POWER button will.
 
I've searched the web, and found this is a common problem with Ivy Bridge motherboards (oh great!).
[http://intellinuxgraphics.org/2012.02.html](http://intellinuxgraphics.org/2012.02.html)
 
[INDENT]*Additionally, the following stability patches are currently available in the **drm-intel-fixes** branch and should be available on the stable **3.2.x** kernel after this release:*
[LIST]
[*]*Stability fixes for hard hangs on Ivy Bridge platform: those patches fix occasional hard-hangs on Ivy Bridge platforms when running GL workloads:*[*patch 1*]("http://lists.freedesktop.org/archives/intel-gfx/2012-February/015000.html")*,*[*patch 2*]("http://lists.freedesktop.org/archives/intel-gfx/2012-February/015001.html")*,*[*patch 3*]("http://lists.freedesktop.org/archives/intel-gfx/2012-February/015002.html")*,*[*patch 4*]("http://lists.freedesktop.org/archives/intel-gfx/2012-February/015003.html")*.*
[/LIST][/INDENT]So I downloaded the Ubuntu source, compiled it, patched the drm-intel fixes, recompiled the kernel; installed it.  Then I updated the libdrm as instructed at the site mentioned above.  But none of it has helped.  I'm still getting DRM errors in Xorg log file, and still getting occasional hard hangs.  It's forced me to run in terminal mode until this is sorted out.
 
Motherboard:  Asus P7Z77-V Pro
CPU:  Intel i7 3770K
Memory:  16GB DDR3 1600M
Boot disk:  Crucial M4 256GB
Swap disk:  256GB SATA
 
Log files:
[http://www.rcollins.org/public/Asus/](http://www.rcollins.org/public/Asus/)
 
It looks like the Intel Ivy Bridge support has been churning for a while.  Has it stabilized?  Is there a known solution to this, further patches.  Any ideas?

---

