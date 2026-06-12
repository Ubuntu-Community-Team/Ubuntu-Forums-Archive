---
title: "LTSP client X11 crash: out of memory"
date: 2006-09-24
forum: Desktop Environments
---

### Post by fnjordy on 2006-09-24
Loading up this big page in Firefox crashes my LTSP client:

[http://doc.m0n0.ch/handbook-single/](http://doc.m0n0.ch/handbook-single/)

The machine has 128MB memory, 8MB video memory, and X11 seems to allocate 64MB memory according to the log.  "dmesg" notes Xorg grew too big and got reaped.

(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 12288 kB
(II) I810(0): VESA VBE OEM: Intel(r)845G/845GL/845GE/845GV Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(r)845G/845GL/845GE/845GV Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): Integrated Graphics Chipset: Intel(R) 845G
(--) I810(0): Chipset: "845G"
(--) I810(0): Linear framebuffer at 0xE0000000
(--) I810(0): IO registers at addr 0xEC100000
(II) I810(0): 1 display pipe available.
(II) I810(0): detected 8060 kB stolen memory.
(WW) I810(0): Detected stolen memory (8000 kB) doesn't match what the BIOS reports (12288 kB)
(II) I810(0): Kernel reported 22016 total, 1 used
(II) I810(0): Checking Available AGP Memory: 88060 kB available (total 88064 kB, used 4 kB)
(--) I810(0): Pre-allocated VideoRAM: 8060 kByte
(==) I810(0): VideoRAM: 65536 kByte

Is there any way to limit the memory used by Xorg?

[17179636.596000] Out of Memory: Killed process 3407 (Xorg).

---

### Post by fnjordy on 2006-09-24
Looks like detection of videoram is faulty.  Setting it explicitly to 8192 works fine, but MueKow doesn't support X_VIDEORAM so I modified ltsp-client-setup to support it:

```

--- ltsp-client-setup.original  2006-09-25 09:25:03.000000000 +0800
+++ ltsp-client-setup   2006-09-25 09:26:35.000000000 +0800
@@ -122,6 +122,9 @@
         preseed $xserver_package $xserver_package/autodetect_video_card "false"
         preseed $xserver_package $xserver_package/config/device/driver "$XSERVER"
       fi
+      if [ -n "$X_VIDEORAM" ]; then
+        preseed $xserver_package $xserver_package/config/device/video_ram $X_VIDEORAM
+      fi
       if [ -n "$X_HORZSYNC" ] && [ -n "$X_VERTREFRESH" ]; then
         preseed $xserver_package $xserver_package/autodetect_monitor "false"
         preseed $xserver_package $xserver_package/config/monitor/selection-method "Advanced"

```

---

