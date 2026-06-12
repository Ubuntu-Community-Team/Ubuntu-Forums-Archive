---
title: "Black Screen At Boot on DELL Studio XPS 13"
date: 2011-07-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by vsoch on 2011-07-07
I have recently installed Ubuntu 11.04 (Natty Narwhal) onto my [COLOR="DarkOrchid"]DELL Studio XPS 13 laptop[/COLOR].  I installed from a USB stick created from the instructions on the site, and installed to the entirely of a 500GB drive.  There is no dual boot.

It only boots all the way to the Ubuntu login screen, maybe 30% of the time, and it's more likely to work after a soft boot.  The boot sequence looks like this:

1) Dell BIOS screen (F12 or F2 for boot settings / setup)
2) Ubuntu purple screen, holds for about 10-15 seconds
3) 
(30% of the time) I see a black screen, then a lit up black screen, and then I hold my breath and it transitions to the Ubuntu splash.  I never see the actual ubuntu name over purple, and I expected that. OR 

(70% of the time) it either flashes from black to black lit 4 times, and remains on the black lit with a single flashing line for... eternity.  I can then hit Control Alt Delete and I see a Flash of the ubuntu logo on purple and text, and it restarts.

Once I am in, things run smoothly... I haven't had crashes or freezes.. yet :P

**WHAT I HAVE TRIED:**
[COLOR="Blue"]Accessing Grub:[/COLOR] I have also tried lightly hitting shift or ESC during this process in an attempt to access grub, and that never has worked.  I think once I might have seen GRUB flash on the screen, but then it jumped to the login splash.

[COLOR="blue"]Is it a problem with the harddisk?[/COLOR]: The SMART checking utility gives me a red warning for 4 bad sectors, although the drive passes.  I also checked my drive with smartctl and can share those report files if anyone needs.  I was thinking if one of the bad sectors happened to be in a place that has an essential pointer for getting from some step n to n+1 in the boot process, that might make it hang up.

[COLOR="blue"]Is it a problem with graphics card?[/COLOR] I found these files that (I think) show the current boot, X.org.0.log and X.org.0.log.old.  It looks like there are errors with nvidia, and something called nr?  I have both those docs to share if anyone might look, and I also put together a doc that details my system hardware.  I should also note that the Xorg files go from 0 to 5, and I'm guessing the other ones are for later in the boot process? Yeah no idea :P

Since this is one of those "proprietary hardware" issues, it was the case that when I first started up, it listed a few graphic drivers under the "Additional Drivers" modules popup.  I wound up choosing the recommended one, and after downloading the files, the bubble turned green, but I realize that at the bottom it says "activated but not in use" (see attached image).  Maybe this is part of the problem?  I'm not even sure where to go to see what drivers are active, and I'm not comfortable enough with linux to try switching anything, at risk of it not booting at all!

Any help would be greatly appreciated.  I am hoping that there is something specific to a hardware driver / Dell that I am missing, and the fix is easy!  I would also want to know if my hard disk is about to fail, so I can get a new one asap.  

I am a graduate student and have lots of work to do, and this has definitely put a damper in my productivity.  I switched from Windows to Linux just yesterday, so this is all very new.  I'd like to get this figured out, for the peace of mind of knowing that my hard disk isn't about to fail, and to have a reliable system to focus on my research.

I am attaching:
additional_drivers.png (shows the status of nvidia drivers)
Xorg.0.old.txt I'm not sure what the difference is between this one and the one without old, but this is the one that is shorter, and has error. I can post the text to the other one if anyone would like to see!
lspi-vvnn.txt: Hardware

Best,

V

---

### Post by mikewhatever on 2011-07-11
Here is the interesting part of Xorg.log:

[noparse]
[    24.647] (EE) NVIDIA(GPU-1): Failed to initialize the NVIDIA GPU at PCI:2:0:0.  Please
[    24.647] (EE) NVIDIA(GPU-1):     check your system's kernel log for additional error
[    24.647] (EE) NVIDIA(GPU-1):     messages and refer to Chapter 8: Common Problems in the
[    24.647] (EE) NVIDIA(GPU-1):     README for additional information.
[    24.647] (EE) NVIDIA(GPU-1): Failed to initialize the NVIDIA graphics device!
[    24.647] 
Backtrace:
[    24.647] 0: /usr/bin/X (xorg_backtrace+0x3b) [0x80eab2b]
[    24.647] 1: /usr/bin/X (0x8048000+0x5fad8) [0x80a7ad8]
[    24.647] 2: (vdso) (__kernel_rt_sigreturn+0x0) [0xb770840c]
[    24.647] Segmentation fault at address (nil)
[    24.647] 
Caught signal 11 (Segmentation fault). Server aborting
[/noparse]

---

### Post by vsoch on 2011-07-11
The issue was 100% driver related.  The fix was to disable/delete the noveau driver from the Synaptic Package Manager (which I think is ubuntu's open source version of the equivalent for nvidia) and then have the following installed / enabled:

nvidia-common
nvidia-settings
nvidia-173

The one that was recommended, nvidia-current, should not be active.  I tried various combinations of nvidia drivers (there are a gazillion) and even though it seems that nvidia-current SHOULD be used, this was the one that was failing at startup.  I don't claim to understand the fix, but my computer starts smoothly and error free at this point, so I'm happy with the fix!

---

### Post by mikewhatever on 2011-07-11
Odd. I would have assumed that Geforce 9400 should work well with the 270.xxx driver.

---

