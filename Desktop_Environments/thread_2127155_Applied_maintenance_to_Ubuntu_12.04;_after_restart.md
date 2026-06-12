---
title: "Applied maintenance to Ubuntu 12.04; after restart my desktop is not responding"
date: 2013-03-19
forum: Desktop Environments
---

### Post by jcanipe on 2013-03-19
On 3/18/13 I got the normal System Update icon that denotes fixes to be applied (I had just applied maintenance a few days earlier). One of the fixes was for a new linuximg...39. After doing the required Restart, the system appears to come up fine. I enter userid/pwd and now my desktop appears. If I start clicking on icons to start (i.e. Chrome, System Settings, basically anything), I do notice that the screen will go blank and then reappear. I can get things to start but eventually they become unresponsive. Eventually I am unable to get any tasks to start. The mouse works fine but the tasks will not start when I click on them. I am unable to do anything after a few minutes. 

On the flip side, if I boot; enter userid/pwd and then wait for a minute, I am unable to start any tasks at all. Once again, the mouse works fine, but NONE of the ICONs will allow me to start any tasks. This also includes: time, ethernet connection, volume... Nothing is reacting to mouse clicks.

I am able to telnet into my machine from my Ubuntu laptop (and I will not be applying the latest maintence to that machine.

Specs: I am running a single image desktop; no other operating system on this computer. When I boot, I do not get a grub menu for selecting an OS; it starts Ubuntu 12.04 (64 bit). Hardward 8GB RAM; 750 GB DASD; Intel I5.

Any suggestions?

---

### Post by steeldriver on 2013-03-19
Even on a single-boot setup you should be able to get the grub menu by holding the shift key right after the BIOS POST screen - then select your last good kernel

Can you open a terminal via Ctrl-Alt-t in the broken desktop? if so you could try resetting unity:

[http://www.webupd8.org/2011/04/how-to-reset-unity-launcher-icons-or.html](http://www.webupd8.org/2011/04/how-to-reset-unity-launcher-icons-or.html)

---

### Post by jcanipe on 2013-03-19
Thanks for the info. I will try the Shift during boot option to see if by selecting linuximg...38 will correct the issue. Regarding resetting Unity, I may give that a try as well. Currently I am unable to get Ctrl-Alt-Del, or any other keyboard sequences I've tried, to respond. However, I have not tried the keyboard sequence mentioned in the link. I can always telnet into this machine and try resetting Unity that way.

---

### Post by jcanipe on 2013-03-19
This also appears to the the same issue under the General tab: [http://ubuntuforums.org/showthread.php?t=2127138](http://ubuntuforums.org/showthread.php?t=2127138)

---

### Post by jcanipe on 2013-03-19
I did use the Shift key during boot (post phase). I got a list of my previous kernels. I selected [FONT=Calibri]3.2.0-38 and it works great (again). [/FONT]

---

### Post by clusia on 2013-03-19
I have the same problem, screen flickering and unresponsive after 30 seconds. Kernel 3.2.0-38 works fine but when I opened log viewer permissions were denied to auth mail and sys.log.

---

### Post by kweinber on 2013-03-20
The update to 3.2.0-39-generic did exactly the same thing to me.  I had to downgrade to 3.2.0-38-generic to get my system stable again.

I am using the standard intel driver.  The bug is triggered by anything accelerated (Java app/chrome/ etc.).

This seems like a major problem with 12.04 stability and Canonical should review this urgently since the update came out last night and will probably start affecting a ton of users.

Here was the sadness in my XOrg log.
 Backtrace:[   587.765] 0: /usr/bin/X (xorg_backtrace+0x26) [0x7fc6ff6749e6]
[   587.765] 1: /usr/bin/X (mieqEnqueue+0x263) [0x7fc6ff6550c3]
[   587.765] 2: /usr/bin/X (0x7fc6ff4ec000+0x62a34) [0x7fc6ff54ea34]
[   587.765] 3: /usr/lib/xorg/modules/input/evdev_drv.so (0x7fc6f94ae000+0x5d88) [0x7fc6f94b3d88]
[   587.765] 4: /usr/bin/X (0x7fc6ff4ec000+0x8af37) [0x7fc6ff576f37]
[   587.765] 5: /usr/bin/X (0x7fc6ff4ec000+0xb0d3a) [0x7fc6ff59cd3a]
[   587.765] 6: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7fc6fe812000+0xfcb0) [0x7fc6fe821cb0]
[   587.765] 7: /lib/x86_64-linux-gnu/libc.so.6 (ioctl+0x7) [0x7fc6fd76e527]
[   587.765] 8: /usr/lib/x86_64-linux-gnu/libdrm.so.2 (drmIoctl+0x28) [0x7fc6fbcff2b8]
[   587.765] 9: /usr/lib/x86_64-linux-gnu/libdrm_intel.so.1 (0x7fc6fb684000+0x8d9a) [0x7fc6fb68cd9a]
[   587.765] 10: /usr/lib/x86_64-linux-gnu/libdrm_intel.so.1 (0x7fc6fb684000+0x8f58) [0x7fc6fb68cf58]
[   587.765] 11: /usr/lib/xorg/modules/drivers/intel_drv.so (0x7fc6fb8a4000+0xb462) [0x7fc6fb8af462]
[   587.765] 12: /usr/lib/xorg/modules/drivers/intel_drv.so (0x7fc6fb8a4000+0x2372a) [0x7fc6fb8c772a]
[   587.765] 13: /usr/lib/xorg/modules/drivers/intel_drv.so (0x7fc6fb8a4000+0xabf3) [0x7fc6fb8aebf3]
[   587.765] 14: /usr/lib/xorg/modules/drivers/intel_drv.so (0x7fc6fb8a4000+0x3888d) [0x7fc6fb8dc88d]
[   587.765] 15: /usr/bin/X (0x7fc6ff4ec000+0x1165c4) [0x7fc6ff6025c4]
[   587.765] 16: /usr/lib/xorg/modules/drivers/intel_drv.so (0x7fc6fb8a4000+0x39be8) [0x7fc6fb8ddbe8]
[   587.765] 17: /usr/bin/X (0x7fc6ff4ec000+0x10f271) [0x7fc6ff5fb271]
[   587.765] 18: /usr/bin/X (0x7fc6ff4ec000+0x4e8a1) [0x7fc6ff53a8a1]
[   587.765] 19: /usr/bin/X (0x7fc6ff4ec000+0x3d7ba) [0x7fc6ff5297ba]
[   587.765] 20: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xed) [0x7fc6fd6a376d]
[   587.765] 21: /usr/bin/X (0x7fc6ff4ec000+0x3daad) [0x7fc6ff529aad]
[   587.765] [mi] These backtraces from mieqEnqueue may point to a culprit higher up the stack.
[   587.765] [mi] mieq is *NOT* the cause.  It is a victim.

---

### Post by jcanipe on 2013-05-01
I decided to bypass using the 3.2... kernel. Instead I used Synaptic to apply the package: linux-generic-lts-quantal. This is currently bringing in the 3.5... version of the kernel. I Just applied latest kernel 3.5.0.28 and the problem seems to have been fixed. Here is the message from my dpkg log file after the maintenace was applied using the update manager: upgrade linux-image-generic-lts-quantal 3.5.0.27.34 3.5.0.28.35.

---

### Post by vbalsys on 2013-05-02
I confirm, that switching to 3.5.0-28-generic kernel has resolved the problem.

Previously tried all kernels from 3.2 branch - no joy. 3.5.0-27 also didn't help.

---

