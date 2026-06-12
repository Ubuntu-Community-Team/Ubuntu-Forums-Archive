---
title: "System occasionally freezes for a few seconds"
date: 2023-05-17
forum: Desktop Environments
---

### Post by jet-bundle on 2023-05-17
I have a new Dell XPS 13 Plus. It came with Ubuntu pre-loaded, but as I've been using Lubuntu for many years I installed Lubuntu 22.04 (5.19.0-41) on a separate partition and have been using that for the past week.

Occasionally the system freezes for maybe seven or eight seconds. The mouse pointer moves, but nothing else happens, although clicks and keystrokes (and scrollwheel turns on my USB mouse) are clearly being buffered as they are implemented as soon as the system unfreezes. So far I've noticed this in three applications: wren scrolling in Evince and in the TexWorks entry window, and when clicking to download pdf files in Firefox.

I'd be grateful for any suggestions on how I could try to pin down the problem.

---

### Post by TheFu on 2023-05-17
Check the system log files.  Google "ubuntu logs" if you don't know how.

---

### Post by guiverc on 2023-05-17
Depending on the RAM & how you use your system (ie. *what apps you have co-existing in RAM & how that compares with the RAM in your hardware*), have you changed the *swap* to better suit your usage?

I find the default is far too small; but currently *`calamares`* or the installer Lubuntu uses does not allow change except *swap on/off* with size being preset. My performance increases when I enlarge the default swap.

Maybe helpful - [https://discourse.lubuntu.me/t/swap-and-lubuntu-faq/2591](https://discourse.lubuntu.me/t/swap-and-lubuntu-faq/2591)

---

### Post by jet-bundle on 2023-05-18
Thank you both for the suggestions. I wonder if the following extract from the output of *sudo dmesg*  might give a clue to the problem? (the complete output is in [https://paste.ubuntu.com/p/4HDzfnxgXC/](https://paste.ubuntu.com/p/4HDzfnxgXC/)
```
[ 6759.674200] i915 0000:00:02.0: [drm] GPU HANG: ecode 12:0:00000000
[ 6759.674388] i915 0000:00:02.0: [drm] Resetting chip for stopped heartbeat on rcs0
[ 6759.777929] i915 0000:00:02.0: [drm] GuC firmware i915/adlp_guc_70.1.1.bin version 70.1
[ 6759.777934] i915 0000:00:02.0: [drm] HuC firmware i915/tgl_huc_7.9.3.bin version 7.9
[ 6759.794508] i915 0000:00:02.0: [drm] HuC authenticated
[ 6759.794924] i915 0000:00:02.0: [drm] GuC submission enabled
[ 6759.794925] i915 0000:00:02.0: [drm] GuC SLPC enabled
```
As far as the swapfile is concerned, I see that its size is 512MB, so that's rather small. But would  I even be using the swapfile? (I have 16GB memory.)

---

### Post by jet-bundle on 2023-05-18
The GPU hang does seem a plausible cause. The system froze just now, and when it unfroze I checked with dmesg and the most recent entries were the same as those I posted above (apart from the timecode, of course).

If that is indeed the case, I wonder if the underlying cause is more likely to be a software problem or a hardware problem?

---

### Post by TheFu on 2023-05-18
> **jet-bundle said:**
> Thank you both for the suggestions. I wonder if the following extract from the output of *sudo dmesg*  might give a clue to the problem? (the complete output is in [https://paste.ubuntu.com/p/4HDzfnxgXC/](https://paste.ubuntu.com/p/4HDzfnxgXC/)
```
[ 6759.674200] i915 0000:00:02.0: [drm] GPU HANG: ecode 12:0:00000000
[ 6759.674388] i915 0000:00:02.0: [drm] Resetting chip for stopped heartbeat on rcs0
[ 6759.777929] i915 0000:00:02.0: [drm] GuC firmware i915/adlp_guc_70.1.1.bin version 70.1
[ 6759.777934] i915 0000:00:02.0: [drm] HuC firmware i915/tgl_huc_7.9.3.bin version 7.9
[ 6759.794508] i915 0000:00:02.0: [drm] HuC authenticated
[ 6759.794924] i915 0000:00:02.0: [drm] GuC submission enabled
[ 6759.794925] i915 0000:00:02.0: [drm] GuC SLPC enabled
```
As far as the swapfile is concerned, I see that its size is 512MB, so that's rather small. But would  I even be using the swapfile? (I have 16GB memory.)

Swap gets used in ways that aren't intuitively obvious.  If you track RAM use over time (top/htop/glances), and see that it never goes above 12G used, then I wouldn't worry about swap. Having "some" swap, enables some kernel performance options that would be disabled otherwise.  Over the years, as browsers have bloated out, I've found that 4.1GB is what I setup for swap on all my desktops, regardless of RAM.  There's a thread in these forums from 2020 about swap, the purpose, how it gets used. Could be worth reading.

Those errors are related to the on-board GPU and DRM.  Because it is intel and drivers are included with the linux kernel,  there probably isn't much to be done.  I'd keep looking for other issues in other logs.

Whenever any error shows up in logs, take the exact error and throw it into a google search.
```
i915 0000:00:02.0: [drm] GPU HANG: ecode 12:0:00000000
```  The few other posts about it seem to say that there's nothing that can be done.  Perhaps disabling DRM would be an option to make this go away?  I suppose it depends on what you use the system for.

---

### Post by ActionParsnip on 2023-05-18
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2001914](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2001914)
possibly this.....

---

### Post by jet-bundle on 2023-05-18
Thanks again for the suggestions. I'll see what happens over the next few days and report back. According to glances, I'm not using swap at all, and memory use rarely goes over a gigabyte (though I haven't tested it when watching video -- but then the problem appeared without using, say, VLC). So I suspect the problem isn't caused by a small swapfilke.

I did note one comment suggesting adding i915.enable_psr=0 to the GRUB_CMDLINE_LINUX_DEFAULT string in /etc/default/grub, so I might try that if the problem reappears.

---

### Post by jet-bundle on 2023-05-19
Adding i915.enable_psr=0 in /etc/default/grub doesn't solve the problem, so I've deleted it.

---

### Post by jet-bundle on 2023-05-24
I've been in touch with Dell Support, who pointed me to a BIOS update. I've installed that through the procedure they suggested (download XPS_9320_2_2_1.exe and copy to a FAT32-formatted USB stick, then reboot and press F12 to reach the one-time boot screen, and finally select Bios Update). There seem to be fewer freezes, but they still occur sometimes.

I have, though, found an alternative driver, oem-somerville-tentacool-meta, so I've installed that and I'll see if the problem goes away completely. If it doesn't come back in the next few days, I'll mark the thread as Solved.

---

### Post by jet-bundle on 2023-05-31
I believe that the problem has now been solved. In comment #9 I remarked that adding i915.enable_psr=0 to the GRUB_CMDLINE_LINUX_DEFAULT string didn't appear to work; but in fact it does. The reason for the discrepancy was that I have a dual-boot system with two copies of Lubuntu, and two copies of GRUB; and I had made the change to the copy of GRUB which wasn't being used. Now that I have made the change to the correct copy of GRUB the problem has gone away. I also notice that scrolling is much smoother.

---

