---
title: "Dell E193FP Monitor &quot;Cannot Display This Video Mode&quot;"
date: 2009-06-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rlrunyon on 2009-06-05
I'm a newbie to Linux, so bare with me. I have a Dell E193FP 19" monitor on an older Dell XPS 400 computer. When I try to run Warsow my monitor goes black with the message "Cannot Display This Video Mode." I have a Nvidia graphics card using 180.44 driver version. The only other 3D game I've played on Ubuntu is Portal and it runs fine (in Wine of course). I have the latest version of Ubuntu.

---

### Post by coffeeaddict22 on 2009-06-06
have a look in your xorg log (System/Admin/Logfile viewer or in a terminal ```
cat Xorg.0.log
```
Post the output back if you need more help; if it doesn't look like the problem is clear, also have a look with ```
dmesg
```

---

### Post by rlrunyon on 2009-06-06
X.org file said this:

> (II) NVIDIA(0): NVIDIA GPU GeForce 8800 GT (G92) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 62.92.1f.00.51
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 8800 GT at PCI:1:0:0:
(--) NVIDIA(0):     DELL E193FP (CRT-0)
(--) NVIDIA(0): DELL E193FP (CRT-0): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (85, 86); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.> (--) PCI:*(0@1:0:0) nVidia Corporation GeForce 8800 GT rev 162, Mem @ 0xee000000/16777216, 0xc0000000/536870912, 0xec000000/33554432, I/O @ 0x0000dc80/128, BIOS @ 0x????????/131072
(--) PCI: (0@5:2:0) nVidia Corporation NV34 [GeForce FX 5200] rev 161, Mem @ 0xea000000/16777216, 0xe0000000/134217728, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)"dmsg" said this:

> [   11.716299] nvidia: module license 'NVIDIA' taints kernel.
[   11.737433] NVRM: The NVIDIA GeForce FX 5200 GPU installed in this system is
[   11.737435] NVRM:  supported through the NVIDIA 173.14.xx Legacy drivers. Please
[   11.737437] NVRM:  visit [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) for more
[   11.737438] NVRM:  information.  The 180.44 NVIDIA driver will ignore
[   11.737440] NVRM:  this GPU.  Continuing probe...> [   11.985873] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.985883] nvidia 0000:01:00.0: setting latency timer to 64
[   11.986110] NVRM: ignoring the legacy GPU 05:02.0
[   11.986119] nvidia: probe of 0000:05:02.0 failed with error -1
[   11.986158] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009This is the only information I see that would help out any. If you need more, I'm more than willing to cooperate.

---

### Post by coffeeaddict22 on 2009-06-06
Sorry, should have been more specific.  dmesg is where the kernel dumps most of its messages.  Try and start Warsow; once it fails, look in dmesg immediately and the output will relate to the problem (if you're lucky).  BTW, The numbers on the side are seconds of uptime.
You shouldn't have too much trouble running it- there's [this post]("http://www.warsow.net/forum/viewtopic.php?id=17746") on the Warsow site that indicates similiar specs run it fine.
Another place to look for odd settings would be in the NVIDIA display setup.  It's in System/Preferences/ from memory (this PC has an ATI card, they put their display stuff in Applications/Accessories/ , and I'm too lazy to get up...).

---

### Post by rlrunyon on 2009-06-06
Ahhh..  no problem. I understand what it's for now. Got the game to work. I somehow forced it to windowed mode and was able to check the games settings. Weird enough it was set to 800x600 on full screen. Changed it to a higher resolution and went back to full screen and it works now. =D Thanks for all your help. I learned a few things with this experience though. ;)

---

