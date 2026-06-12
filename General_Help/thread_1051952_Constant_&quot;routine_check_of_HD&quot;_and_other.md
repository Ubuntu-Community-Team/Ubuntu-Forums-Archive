---
title: "Constant &quot;routine check of HD&quot; and other quirky behavior"
date: 2009-01-27
forum: General Help
---

### Post by Sweet Spot on 2009-01-27
I'm at a loss for what to think or do. For the past couple of months, no matter when or how often I boot my Ubuntu box, (all new hardware including Mobo and HD) halfway through booting up, the  "routine check of HD sda 3" dialog comes up and starts to do its thing. I always have to hit the esc key to finish the boot process. I know that after every 30 or so boots it will do this automatically, and that's what I am used to, but not every time.  I built this PC less than a year ago, and have had a couple of glitchy things happen with it such as:

When  using DVD Shrink to compress a DVD, it will stop due to some error (likely a dirty disc or the DVD drive not reading properly) which is fine, but when I go to delete the half done ISO, I won't be able to access it at all, because it is grey'd out. I actually wouldn't be able to acess any file from that directory, until I reboot the system. That's one thing. 

I sometimes play Urban Terror, and have never had it crash on me in the middle of playing before, up until this phenomenon. I'll be playing and, the screen will go blank and the audio will just skip/repeat until I reboot.  I'm using the MOBO's graphics chip which is made by ATI. I bought an Nvidia card, but don't want to install it until I figure out what is up with my current configuration. 

#3 When installing Ubuntu, I was having a lot of problems with my DVD drive not reading the discs. I had to play around with ejecting and putting them back, and ultimately decided to disconnect the SATA cable from its spot on the MOBO and put it into another slot, which worked. I just wonder if the MOBO its self is the root of all my problems, or perhaps a couple of bad SATA cables ? (doubt that though)


I took a look at my most recent activity log and saw a few things which might be odd, but don't know for sure:

> Jan 27 08:58:06 dougb-desktop kernel: [   18.993801] Checking aperture...
Jan 27 08:58:06  [   18.993803] CPU 0: aperture @ 40000000 size 32 MB
Jan 27 08:58:06  kernel: [   18.993804] Aperture too small (32 MB)
Jan 27 08:58:06 -desktop kernel: [   19.003106] No AGP bridge found
Jan 27 08:58:06 -desktop kernel: [   19.003108] Your BIOS doesn't leave a aperture memory hole
Jan 27 08:58:06-desktop kernel: [   19.003109] Please enable the IOMMU option in the BIOS setup
Jan 27 08:58:06 -desktop kernel: [   19.003110] This costs you 64 MB of RAM
Jan 27 08:58:06 -desktop kernel: [   19.028197] Mapping aperture over 65536 KB of RAM @ 4000000
Jan 27 08:58:06desktop kernel: [   19.028201] swsusp: Registered nosave memory region: 0000000004000000 - 0000000008000000

> Jan 27 09:22:41 dougb-desktop kernel: [  925.455286] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Jan 27 09:22:41 dougb-desktop kernel: [  925.456403] ata1.00: configured for UDMA/33
Jan 27 09:22:41 dougb-desktop kernel: [  925.456410] ata1: EH complete
Jan 27 09:22:41 dougb-desktop kernel: [  925.456442] sd 1:0:0:0: [sda] 1250263728 512-byte hardware sectors (640135 MB)
Jan 27 09:22:41 dougb-desktop kernel: [  925.456452] sd 1:0:0:0: [sda] Write Protect is off
Jan 27 09:22:41 dougb-desktop kernel: [  925.456467] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 27 09:22:47 dougb-desktop kernel: [  931.084442]          res 40/00:84:3f:1f:68/00:00:00:00:00/40 Emask 0x52 (ATA bus error)
Jan 27 09:22:47 dougb-desktop kernel: [  931.084449]          res 40/00:84:3f:1f:68/00:00:00:00:00/40 Emask 0x52 (ATA bus error)
Jan 27 09:22:47 dougb-desktop kernel: [  931.084456]          res 40/00:84:3f:1f:68/00:00:00:00:00/40 Emask 0x52 (ATA bus error)
Jan 27 09:22:47 dougb-desktop kernel: [  931.084462]          res 40/00:84:3f:1f:68/00:00:00:00:00/40 Emask 0x52 (ATA bus error)
Jan 27 09:22:47 dougb-desktop kernel: [  931.084469]          res 40/00:84:3f:1f:68/00:00:00:00:00/40 Emask 0x52 (ATA bus error)
Jan 27 09:22:47 dougb-desktop kernel: [  931.084475]          res 40/00:84:3f:1f:68/00:00:00:00:00/40 Emask 0x52 (ATA bus error)
Jan 27 09:22:47 dougb-desktop kernel: [  931.084481]          res 40/00:84:3f:1f:68/00:00:00:00:00/40 Emask 0x52 (ATA bus error)
Jan 27 09:22:47 dougb-desktop kernel: [  931.084488]          res 40/00:84:3f:1f:68/00:00:00:00:00/40 Emask 0x52 (ATA bus error)
Jan 27 09:22:47 dougb-desktop kernel: [  931.084494]          res 40/00:84:3f:1f:68/00:00:00:00:00/40 Emask 0x52 (ATA bus error)
Jan 27 09:22:47 dougb-desktop kernel: [  931.084501]          res 40/00:84:3f:1f:68/00:00:00:00:00/40 Emask 0x52 (ATA bus error)
Jan 27 09:22:47 dougb-desktop kernel: [  931.084507]          res 40/00:84:3f:1f:68/00:00:00:00:00/40 Emask 0x52 (ATA bus error)
Jan 27 09:22:47 dougb-desktop kernel: [  931.084513]          res 40/00:84:3f:1f:68/00:00:00:00:00/40 Emask 0x52 (ATA bus error)
Jan 27 09:22:47 dougb-desktop kernel: [  931.084520]          res 40/00:84:3f:1f:68/00:00:00:00:00/40 Emask 0x52 (ATA bus error)
Jan 27 09:22:47 dougb-desktop kernel: [  931.084526]          res 40/00:84:3f:1f:68/00:00:00:00:00/40 Emask 0x52 (ATA bus error)
Jan 27 09:22:47 dougb-desktop kernel: [  931.084532]          res 40/00:84:3f:1f:68/00:00:00:00:00/40 Emask 0x52 (ATA bus error)
Jan 27 09:22:47 dougb-desktop kernel: [  931.084539]          res 40/00:84:3f:1f:68/00:00:00:00:00/40 Emask 0x52 (ATA bus error)
Jan 27 09:22:47 dougb-desktop kernel: [  931.084545]          res 40/00:84:3f:1f:68/00:00:00:00:00/40 Emask 0x52 (ATA bus error)
Jan 27 09:22:47 dougb-desktop kernel: [  931.084552]          res 40/00:84:3f:1f:68/00:00:00:00:00/40 Emask 0x52 (ATA bus error)
Jan 27 09:22:47 dougb-desktop kernel: [  931.084558]          res 40/00:84:3f:1f:68/00:00:00:00:00/40 Emask 0x52 (ATA bus error)
Jan 27 09:22:47 dougb-desktop kernel: [  931.084569] ata1: hard resetting link
Jan 27 09:22:47 dougb-desktop kernel: [  931.558878] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Jan 27 09:22:47 dougb-desktop kernel: [  931.560329] ata1.00: configured for UDMA/33
Jan 27 09:22:47 dougb-desktop kernel: [  931.560357] ata1: EH complete
Jan 27 09:22:47 dougb-desktop kernel: [  931.560482] sd 1:0:0:0: [sda] 1250263728 512-byte hardware sectors (640135 MB)
Jan 27 09:22:47 dougb-desktop kernel: [  931.560492] sd 1:0:0:0: [sda] Write Protect is off
Jan 27 09:22:47 dougb-desktop kernel: [  931.560507] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 27 09:22:48 dougb-desktop kernel: [  931.791631]          res 40/00:7c:4f:08:6a/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Jan 27 09:22:48 dougb-desktop kernel: [  931.791638]          res 40/00:7c:4f:08:6a/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Jan 27 09:22:48 dougb-desktop kernel: [  931.791644]          res 40/00:7c:4f:08:6a/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Jan 27 09:22:48 dougb-desktop kernel: [  931.791650]          res 40/00:7c:4f:08:6a/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Jan 27 09:22:48 dougb-desktop kernel: [  931.791657]          res 40/00:7c:4f:08:6a/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Jan 27 09:22:48 dougb-desktop kernel: [  931.791663]          res 40/00:7c:4f:08:6a/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Jan 27 09:22:48 dougb-desktop kernel: [  931.791669]          res 40/00:7c:4f:08:6a/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Jan 27 09:22:48 dougb-desktop kernel: [  931.791676]          res 40/00:7c:4f:08:6a/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Jan 27 09:22:48 dougb-desktop kernel: [  931.791682]          res 40/00:7c:4f:08:6a/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Jan 27 09:22:48 dougb-desktop kernel: [  931.791688]          res 40/00:7c:4f:08:6a/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Jan 27 09:22:48 dougb-desktop kernel: [  931.791695]          res 40/00:7c:4f:08:6a/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Jan 27 09:22:48 dougb-desktop kernel: [  931.791701]          res 40/00:7c:4f:08:6a/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Jan 27 09:22:48 dougb-desktop kernel: [  931.791708]          res 40/00:7c:4f:08:6a/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Jan 27 09:22:48 dougb-desktop kernel: [  931.791714]          res 40/00:7c:4f:08:6a/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Jan 27 09:22:48 dougb-desktop kernel: [  931.791721]          res 40/00:7c:4f:08:6a/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Jan 27 09:22:48 dougb-desktop kernel: [  931.791727]          res 40/00:7c:4f:08:6a/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Jan 27 09:22:48 dougb-desktop kernel: [  931.791733]          res 40/00:7c:4f:08:6a/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Jan 27 09:22:48 dougb-desktop kernel: [  931.791740]          res 40/00:7c:4f:08:6a/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Jan 27 09:22:48 dougb-desktop kernel: [  931.791746]          res 40/00:7c:4f:08:6a/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Jan 27 09:22:48 dougb-desktop kernel: [  931.791757] ata1: hard resetting link
Jan 27 09:22:48 dougb-desktop kernel: [  932.265789] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Jan 27 09:22:48 dougb-desktop kernel: [  932.267245] ata1.00: configured for UDMA/33
Jan 27 09:22:48 dougb-desktop kernel: [  932.267270] ata1: EH complete
Jan 27 09:22:48 dougb-desktop kernel: [  932.267371] sd 1:0:0:0: [sda] 1250263728 512-byte hardware sectors (640135 MB)
Jan 27 09:22:48 dougb-desktop kernel: [  932.267380] sd 1:0:0:0: [sda] Write Protect is off
Jan 27 09:22:48 dougb-desktop kernel: [  932.267395] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 27 09:23:03 dougb-desktop kernel: [  943.938112]          res 40/00:04:7f:ff:4c/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Jan 27 09:23:03 dougb-desktop kernel: [  943.938120] ata1: hard resetting link
Jan 27 09:23:03 dougb-desktop kernel: [  944.412372] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Jan 27 09:23:03 dougb-desktop kernel: [  944.414488] ata1.00: configured for UDMA/33
Jan 27 09:23:03 dougb-desktop kernel: [  944.414496] ata1: EH complete
Jan 27 09:23:03 dougb-desktop kernel: [  944.414527] sd 1:0:0:0: [sda] 1250263728 512-byte hardware sectors (640135 MB)
Jan 27 09:23:03 dougb-desktop kernel: [  944.414537] sd 1:0:0:0: [sda] Write Protect is off
Jan 27 09:23:03 dougb-desktop kernel: [  944.414552] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 27 09:23:04 dougb-desktop kernel: [  944.496246]          res 40/00:14:77:8e:21/00:00:01:00:00/40 Emask 0x50 (ATA bus error)
Jan 27 09:23:04 dougb-desktop kernel: [  944.496253]          res 40/00:14:77:8e:21/00:00:01:00:00/40 Emask 0x50 (ATA bus error)
Jan 27 09:23:04 dougb-desktop kernel: [  944.496259]          res 40/00:14:77:8e:21/00:00:01:00:00/40 Emask 0x50 (ATA bus error)
Jan 27 09:23:04 dougb-desktop kernel: [  944.496268] ata1: hard resetting link
Jan 27 09:23:04 dougb-desktop kernel: [  944.553345] [fglrx] interrupt source ff00002f successfully disabled!
Jan 27 09:23:04 dougb-desktop kernel: [  944.553351] [fglrx] enable ID = 0x00000000
Jan 27 09:23:04 dougb-desktop kernel: [  944.553353] [fglrx] Receive disable interrupt message with irqEnableMask: ff00002f; dwIRQEnableId: 00000006
Jan 27 09:23:04 dougb-desktop kernel: [  944.968021] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)

> Jan 27 09:06:57 dougb-desktop kernel: [  371.037936] ata3: SATA link down (SStatus 0 SControl 300)
Jan 27 09:06:57 dougb-desktop kernel: [  371.037946] ata3: EH complete
Jan 27 09:06:58 dougb-desktop kernel: [  372.171606] ata3: soft resetting link
Jan 27 09:06:58 dougb-desktop kernel: [  372.171624] ata3: SATA link down (SStatus 0 SControl 300)
Jan 27 09:06:58 dougb-desktop kernel: [  372.171634] ata3: EH complete
Jan 27 09:07:00 dougb-desktop kernel: [  372.818778] ata3: soft resetting link
Jan 27 09:07:00 dougb-desktop kernel: [  372.818788] ata3: SATA link down (SStatus 0 SControl 300)
Jan 27 09:07:00 dougb-desktop kernel: [  372.818795] ata3: EH complete
Jan 27 09:07:00 dougb-desktop kernel: [  373.171779] ata3: soft resetting link
Jan 27 09:07:00 dougb-desktop kernel: [  373.171788] ata3: SATA link down (SStatus 0 SControl 300)

Anything alarming in those messages ? And, is there anything else I can do, to test my hardware for serious problems ? Something for the MOBO ? 

Thanks for looking. 

Doug

---

### Post by Sweet Spot on 2009-01-27
Nothing ?

---

### Post by dcstar on 2009-01-28
> **Sweet Spot said:**
> 
.........
Anything alarming in those messages ? And, is there anything else I can do, to test my hardware for serious problems ? Something for the MOBO ? 
..........

Firstly, please DON'T "quote" data, that is for previous text, use the Code tags.

Secondly, those messages indicate major problems with the MB/Drive interface and will probably leave you with a permanently broken or unreliable system.

It may be the kernel you are using, but it is probably something in your hardware, you may have to start swapping out components to see if it goes away. You can also reset your BIOS to defaults to see if that helps.

---

