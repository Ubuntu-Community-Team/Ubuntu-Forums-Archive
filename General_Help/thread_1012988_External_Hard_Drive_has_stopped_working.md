---
title: "External Hard Drive has stopped working"
date: 2008-12-16
forum: General Help
---

### Post by corwinspyre on 2008-12-16
Hi everyone,

I'm having a strange problem.  I normally run a computer with external hard drives and a laptop, both with Ubuntu 8.10.  I'm home for winter break, so I only brought the externals and laptop.  The hard drives worked fine on the computer, but one seemingly cannot be found on my laptop.  It is an IDE hard drive connected via USB2 formatted with NTFS.

What I know:
-It's not the laptop's USB port because the other external hard drive works.
-It doesn't show up via "sudo fdisk -l"
-It also won't work on Vista.  I searched around and there's no reason provided, but it seems sometimes Vista won't read NTFS partitions that XP can.  I verified on another computer that it does indeed show up in Windows XP, with all the data there.  In Vista, it says it needs to be formatted before use.
-It's not dirty.  Originally, I unplugged it after I shut down my computer.  Since then, like I said I tried it on XP and then chose the option to safely remove it.
-Having it plugged in at boot or plugging it in after logging in doesn't matter
-I've used it plenty of times before on the laptop, and I'm not sure what's different about this time.

Help is much appreciated, as I need to do work using files on it!  Please let me know of any other information I should provide.  Thanks!

---

### Post by corwinspyre on 2008-12-16
I found it on /var/log/messages, but not as of the latest reboot.  It's the one marked 500gb.  So I guess it's finding it sometimes.  Here's "cat /var/log/messages | grep sd":
```
Dec 16 10:43:07 midell kernel: [233110.681558] sd 9:0:0:0: [sdc] 976773167 512-byte hardware sectors (500108 MB)
Dec 16 10:43:07 midell kernel: [233110.690004] sd 9:0:0:0: [sdc] Write Protect is off
Dec 16 10:43:07 midell kernel: [233110.698116] sd 9:0:0:0: [sdc] 976773167 512-byte hardware sectors (500108 MB)
Dec 16 10:43:07 midell kernel: [233110.702483] sd 9:0:0:0: [sdc] Write Protect is off
Dec 16 10:43:08 midell kernel: [233110.710388]  sdc: sdc1 < sdc5 >
Dec 16 10:43:08 midell kernel: [233110.816517] sd 9:0:0:0: [sdc] Attached SCSI disk
Dec 16 10:43:08 midell kernel: [233110.818279] sd 9:0:0:0: Attached scsi generic sg3 type 0
Dec 16 10:44:18 midell kernel: [233180.888519] sd 10:0:0:0: [sdc] 976773167 512-byte hardware sectors (500108 MB)
Dec 16 10:44:18 midell kernel: [233180.888519] sd 10:0:0:0: [sdc] Write Protect is off
Dec 16 10:44:18 midell kernel: [233180.912058] sd 10:0:0:0: [sdc] 976773167 512-byte hardware sectors (500108 MB)
Dec 16 10:44:18 midell kernel: [233180.920727] sd 10:0:0:0: [sdc] Write Protect is off
Dec 16 10:44:18 midell kernel: [233180.920900]  sdc: sdc1 < sdc5 >
Dec 16 10:44:18 midell kernel: [233180.931061] sd 10:0:0:0: [sdc] Attached SCSI disk
Dec 16 10:44:18 midell kernel: [233181.041366] sd 10:0:0:0: Attached scsi generic sg3 type 0
Dec 16 10:49:48 midell kernel: [233511.108021] sd 11:0:0:0: [sdc] 976773167 512-byte hardware sectors (500108 MB)
Dec 16 10:49:48 midell kernel: [233511.118666] sd 11:0:0:0: [sdc] Write Protect is off
Dec 16 10:49:48 midell kernel: [233511.130396] sd 11:0:0:0: [sdc] 976773167 512-byte hardware sectors (500108 MB)
Dec 16 10:49:48 midell kernel: [233511.132516] sd 11:0:0:0: [sdc] Write Protect is off
Dec 16 10:49:48 midell kernel: [233511.132516]  sdc: sdc1 < sdc5 >
Dec 16 10:49:48 midell kernel: [233511.164435] sd 11:0:0:0: [sdc] Attached SCSI disk
Dec 16 10:49:48 midell kernel: [233511.164554] sd 11:0:0:0: Attached scsi generic sg3 type 0
Dec 16 10:50:37 midell kernel: [233560.331854] sd 12:0:0:0: [sdc] 976773167 512-byte hardware sectors (500108 MB)
Dec 16 10:50:37 midell kernel: [233560.340539] sd 12:0:0:0: [sdc] Write Protect is off
Dec 16 10:50:37 midell kernel: [233560.344049] sd 12:0:0:0: [sdc] 976773167 512-byte hardware sectors (500108 MB)
Dec 16 10:50:37 midell kernel: [233560.345570] sd 12:0:0:0: [sdc] Write Protect is off
Dec 16 10:50:37 midell kernel: [233560.345595]  sdc: sdc1 < sdc5 >
Dec 16 10:50:37 midell kernel: [233560.372508] sd 12:0:0:0: [sdc] Attached SCSI disk
Dec 16 10:50:37 midell kernel: [233560.372795] sd 12:0:0:0: Attached scsi generic sg3 type 0
Dec 16 10:51:30 midell kernel: [233613.532031] sd 14:0:0:0: [sdc] 976773167 512-byte hardware sectors (500108 MB)
Dec 16 10:51:30 midell kernel: [233613.536062] sd 14:0:0:0: [sdc] Write Protect is off
Dec 16 10:51:30 midell kernel: [233613.542103] sd 14:0:0:0: [sdc] 976773167 512-byte hardware sectors (500108 MB)
Dec 16 10:51:30 midell kernel: [233613.544055] sd 14:0:0:0: [sdc] Write Protect is off
Dec 16 10:51:30 midell kernel: [233613.544055]  sdc: sdc1 < sdc5 >
Dec 16 10:51:30 midell kernel: [233613.591320] sd 14:0:0:0: [sdc] Attached SCSI disk
Dec 16 10:51:30 midell kernel: [233613.592020] sd 14:0:0:0: Attached scsi generic sg3 type 0
Dec 16 10:54:55 midell kernel: [    7.936520] Driver 'sd' needs updating - please use bus_type methods
Dec 16 10:54:55 midell kernel: [    7.936520] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
Dec 16 10:54:55 midell kernel: [    7.936520] sd 0:0:0:0: [sda] Write Protect is off
Dec 16 10:54:55 midell kernel: [    7.936520] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 16 10:54:55 midell kernel: [    7.936601] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
Dec 16 10:54:55 midell kernel: [    7.936672] sd 0:0:0:0: [sda] Write Protect is off
Dec 16 10:54:55 midell kernel: [    7.936745] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 16 10:54:55 midell kernel: [    7.936753]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Dec 16 10:54:55 midell kernel: [    8.016976]  sda1 sda2 sda3 sda4
Dec 16 10:54:55 midell kernel: [    8.017448] sd 0:0:0:0: [sda] Attached SCSI disk
Dec 16 10:54:55 midell kernel: [   14.410850] sd 8:0:0:0: [sdb] 976773167 512-byte hardware sectors (500108 MB)
Dec 16 10:54:55 midell kernel: [   14.411725] sd 8:0:0:0: [sdb] Write Protect is off
Dec 16 10:54:55 midell kernel: [   14.412844] sd 8:0:0:0: [sdb] 976773167 512-byte hardware sectors (500108 MB)
Dec 16 10:54:55 midell kernel: [   14.413717] sd 8:0:0:0: [sdb] Write Protect is off
Dec 16 10:54:55 midell kernel: [   14.413747]  sdb: sdb1 < sdb5 >
Dec 16 10:54:55 midell kernel: [   14.420925] sd 8:0:0:0: [sdb] Attached SCSI disk
Dec 16 10:54:55 midell kernel: [   14.421295] sd 8:0:0:0: Attached scsi generic sg2 type 0
Dec 16 10:54:55 midell kernel: [   14.423539] sd 9:0:0:0: [sdc] Attached SCSI removable disk
Dec 16 10:54:55 midell kernel: [   14.423791] sd 9:0:0:0: Attached scsi generic sg3 type 0
Dec 16 10:54:55 midell kernel: [   21.814458] EXT3 FS on sda3, internal journal
Dec 16 10:54:55 midell kernel: [   22.799302] EXT3 FS on sda4, internal journal
Dec 16 10:54:55 midell kernel: [   26.740104] type=1505 audit(1229446493.207:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4492
Dec 16 11:10:32 midell kernel: [    7.512550] Driver 'sd' needs updating - please use bus_type methods
Dec 16 11:10:32 midell kernel: [    7.512550] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
Dec 16 11:10:32 midell kernel: [    7.512550] sd 0:0:0:0: [sda] Write Protect is off
Dec 16 11:10:32 midell kernel: [    7.512550] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 16 11:10:32 midell kernel: [    7.512550] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
Dec 16 11:10:32 midell kernel: [    7.512550] sd 0:0:0:0: [sda] Write Protect is off
Dec 16 11:10:32 midell kernel: [    7.512550] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 16 11:10:32 midell kernel: [    7.512550]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Dec 16 11:10:32 midell kernel: [    7.586149]  sda1 sda2 sda3 sda4
Dec 16 11:10:32 midell kernel: [    7.586599] sd 0:0:0:0: [sda] Attached SCSI disk
Dec 16 11:10:32 midell kernel: [   13.389441] sd 8:0:0:0: [sdb] Attached SCSI removable disk
Dec 16 11:10:32 midell kernel: [   13.389677] sd 8:0:0:0: Attached scsi generic sg2 type 0
Dec 16 11:10:32 midell kernel: [   20.613182] EXT3 FS on sda3, internal journal
Dec 16 11:10:32 midell kernel: [   21.623921] EXT3 FS on sda4, internal journal
Dec 16 11:10:32 midell kernel: [   25.648055] type=1505 audit(1229447430.216:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4470
Dec 16 11:14:43 midell kernel: [    8.923389] Driver 'sd' needs updating - please use bus_type methods
Dec 16 11:14:43 midell kernel: [    8.937432] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
Dec 16 11:14:43 midell kernel: [    8.963741] sd 0:0:0:0: [sda] Write Protect is off
Dec 16 11:14:43 midell kernel: [    9.004219] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 16 11:14:43 midell kernel: [    9.034517] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
Dec 16 11:14:43 midell kernel: [    9.048560] sd 0:0:0:0: [sda] Write Protect is off
Dec 16 11:14:43 midell kernel: [    9.063052] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 16 11:14:43 midell kernel: [    9.093118]  sda:<6>usb 7-1: configuration #1 chosen from 1 choice
Dec 16 11:14:43 midell kernel: [    9.168512]  sda1 sda2 sda3 sda4
Dec 16 11:14:43 midell kernel: [    9.182337] sd 0:0:0:0: [sda] Attached SCSI disk
Dec 16 11:14:43 midell kernel: [   13.676344] sd 8:0:0:0: [sdb] Attached SCSI removable disk
Dec 16 11:14:43 midell kernel: [   13.692250] sd 8:0:0:0: Attached scsi generic sg2 type 0
Dec 16 11:14:43 midell kernel: [   23.193733] EXT3 FS on sda3, internal journal
Dec 16 11:14:43 midell kernel: [   24.080248] EXT3 FS on sda4, internal journal
Dec 16 11:14:43 midell kernel: [   28.024550] type=1505 audit(1229447681.050:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4318
Dec 16 11:18:53 midell kernel: [    8.863232] Driver 'sd' needs updating - please use bus_type methods
Dec 16 11:18:53 midell kernel: [    8.877237] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
Dec 16 11:18:53 midell kernel: [    8.890606] sd 0:0:0:0: [sda] Write Protect is off
Dec 16 11:18:53 midell kernel: [    8.906210] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 16 11:18:53 midell kernel: [    8.948548] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
Dec 16 11:18:53 midell kernel: [    8.948548] sd 0:0:0:0: [sda] Write Protect is off
Dec 16 11:18:53 midell kernel: [    8.948548] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 16 11:18:53 midell kernel: [    8.948548]  sda: sda1 sda2 sda3 sda4
Dec 16 11:18:53 midell kernel: [    9.033448] sd 0:0:0:0: [sda] Attached SCSI disk
Dec 16 11:18:53 midell kernel: [   13.657456] sd 8:0:0:0: [sdb] Attached SCSI removable disk
Dec 16 11:18:53 midell kernel: [   13.672172] sd 8:0:0:0: Attached scsi generic sg2 type 0
Dec 16 11:18:53 midell kernel: [   22.614090] EXT3 FS on sda3, internal journal
Dec 16 11:18:53 midell kernel: [   95.635222] EXT3 FS on sda4, internal journal
Dec 16 11:18:53 midell kernel: [   96.796759] type=1505 audit(1229447930.453:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4323
Dec 16 11:22:49 midell kernel: [    9.063351] Driver 'sd' needs updating - please use bus_type methods
Dec 16 11:22:49 midell kernel: [    9.082200] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
Dec 16 11:22:49 midell kernel: [    9.128449] sd 0:0:0:0: [sda] Write Protect is off
Dec 16 11:22:49 midell kernel: [    9.141431] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 16 11:22:49 midell kernel: [    9.173982] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
Dec 16 11:22:49 midell kernel: [    9.187817] sd 0:0:0:0: [sda] Write Protect is off
Dec 16 11:22:49 midell kernel: [    9.202532] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 16 11:22:49 midell kernel: [    9.233561]  sda:<6>usb 7-1: configuration #1 chosen from 1 choice
Dec 16 11:22:49 midell kernel: [    9.306482]  sda1 sda2 sda3 sda4
Dec 16 11:22:49 midell kernel: [    9.321542] sd 0:0:0:0: [sda] Attached SCSI disk
Dec 16 11:22:49 midell kernel: [   13.774914] sd 8:0:0:0: [sdb] Attached SCSI removable disk
Dec 16 11:22:49 midell kernel: [   13.789585] sd 8:0:0:0: Attached scsi generic sg2 type 0
Dec 16 11:22:49 midell kernel: [   22.777664] EXT3 FS on sda3, internal journal
Dec 16 11:22:49 midell kernel: [   23.655344] EXT3 FS on sda4, internal journal
Dec 16 11:22:49 midell kernel: [   24.888348] type=1505 audit(1229448167.338:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4375
Dec 16 11:56:11 midell kernel: [    9.377409] Driver 'sd' needs updating - please use bus_type methods
Dec 16 11:56:11 midell kernel: [    9.391242] sd 2:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
Dec 16 11:56:11 midell kernel: [    9.404677] sd 2:0:0:0: [sda] Write Protect is off
Dec 16 11:56:11 midell kernel: [    9.421023] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 16 11:56:11 midell kernel: [    9.449175] sd 2:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
Dec 16 11:56:11 midell kernel: [    9.478639] sd 2:0:0:0: [sda] Write Protect is off
Dec 16 11:56:11 midell kernel: [    9.493627] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 16 11:56:11 midell kernel: [    9.524340]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Dec 16 11:56:11 midell kernel: [    9.595875]  sda1 sda2 sda3 sda4
Dec 16 11:56:11 midell kernel: [    9.610805] sd 2:0:0:0: [sda] Attached SCSI disk
Dec 16 11:56:11 midell kernel: [   15.150811] sd 8:0:0:0: [sdb] Attached SCSI removable disk
Dec 16 11:56:11 midell kernel: [   15.166075] sd 8:0:0:0: Attached scsi generic sg2 type 0
Dec 16 11:56:11 midell kernel: [   23.801037] EXT3 FS on sda3, internal journal
Dec 16 11:56:11 midell kernel: [   24.667003] EXT3 FS on sda4, internal journal
Dec 16 11:56:11 midell kernel: [   25.952297] type=1505 audit(1229450169.327:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4373
Dec 16 11:59:12 midell kernel: [    9.212517] Driver 'sd' needs updating - please use bus_type methods
Dec 16 11:59:12 midell kernel: [    9.226250] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
Dec 16 11:59:12 midell kernel: [    9.239744] sd 0:0:0:0: [sda] Write Protect is off
Dec 16 11:59:12 midell kernel: [    9.253070] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 16 11:59:12 midell kernel: [    9.280373] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
Dec 16 11:59:12 midell kernel: [    9.294290] sd 0:0:0:0: [sda] Write Protect is off
Dec 16 11:59:12 midell kernel: [    9.308177] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 16 11:59:12 midell kernel: [    9.336369]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Dec 16 11:59:12 midell kernel: [    9.408109]  sda1 sda2 sda3 sda4
Dec 16 11:59:12 midell kernel: [    9.426460] sd 0:0:0:0: [sda] Attached SCSI disk
Dec 16 11:59:12 midell kernel: [   15.751650] sd 8:0:0:0: [sdb] Attached SCSI removable disk
Dec 16 11:59:12 midell kernel: [   15.766645] sd 8:0:0:0: Attached scsi generic sg2 type 0
Dec 16 11:59:12 midell kernel: [   24.302404] EXT3 FS on sda3, internal journal
Dec 16 11:59:12 midell kernel: [   25.157225] EXT3 FS on sda4, internal journal
Dec 16 11:59:12 midell kernel: [   26.289928] type=1505 audit(1229450350.225:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4316
Dec 16 12:06:02 midell kernel: [    9.298511] Driver 'sd' needs updating - please use bus_type methods
Dec 16 12:06:02 midell kernel: [    9.329763] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
Dec 16 12:06:02 midell kernel: [    9.348359] sd 0:0:0:0: [sda] Write Protect is off
Dec 16 12:06:02 midell kernel: [    9.366728] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 16 12:06:02 midell kernel: [    9.396968] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
Dec 16 12:06:02 midell kernel: [    9.412571] sd 0:0:0:0: [sda] Write Protect is off
Dec 16 12:06:02 midell kernel: [    9.428073] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 16 12:06:02 midell kernel: [    9.458818]  sda:<6>usb 6-1: configuration #1 chosen from 1 choice
Dec 16 12:06:02 midell kernel: [    9.537866]  sda1 sda2 sda3 sda4
Dec 16 12:06:02 midell kernel: [    9.556572] sd 0:0:0:0: [sda] Attached SCSI disk
Dec 16 12:06:02 midell kernel: [   15.373419] sd 8:0:0:0: [sdb] Attached SCSI removable disk
Dec 16 12:06:02 midell kernel: [   15.388125] sd 8:0:0:0: Attached scsi generic sg2 type 0
Dec 16 12:06:02 midell kernel: [   24.088779] EXT3 FS on sda3, internal journal
Dec 16 12:06:02 midell kernel: [   24.964668] EXT3 FS on sda4, internal journal
Dec 16 12:06:02 midell kernel: [   25.968550] type=1505 audit(1229450760.111:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4384
Dec 16 12:09:09 midell kernel: [    8.444555] Driver 'sd' needs updating - please use bus_type methods
Dec 16 12:09:09 midell kernel: [    8.459219] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
Dec 16 12:09:09 midell kernel: [    8.474007] sd 0:0:0:0: [sda] Write Protect is off
Dec 16 12:09:09 midell kernel: [    8.488930] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 16 12:09:09 midell kernel: [    8.517077] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
Dec 16 12:09:09 midell kernel: [    8.531796] sd 0:0:0:0: [sda] Write Protect is off
Dec 16 12:09:09 midell kernel: [    8.546603] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 16 12:09:09 midell kernel: [    8.576322]  sda: sda1 sda2 sda3 sda4
Dec 16 12:09:09 midell kernel: [    8.669243] sd 0:0:0:0: [sda] Attached SCSI disk
Dec 16 12:09:09 midell kernel: [   15.238922] sd 8:0:0:0: [sdb] Attached SCSI removable disk
Dec 16 12:09:09 midell kernel: [   15.254208] sd 8:0:0:0: Attached scsi generic sg1 type 0
Dec 16 12:09:09 midell kernel: [   23.168956] EXT3 FS on sda3, internal journal
Dec 16 12:09:09 midell kernel: [   24.021930] EXT3 FS on sda4, internal journal
Dec 16 12:09:09 midell kernel: [   25.040552] type=1505 audit(1229450947.037:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4247
```

---

### Post by cariboo on 2008-12-16
Could you paste the output of the following command in your next post. Plug your drive in, and in a terminal type the following:

```
demsg | tail -n 10
```

This command will print out the last 10 lines of dmesg, which may give us a clue as to why the drive is not detected.

Jim

---

### Post by corwinspyre on 2008-12-16
> **cariboo907 said:**
> Could you paste the output of the following command in your next post. Plug your drive in, and in a terminal type the following:

```
demsg | tail -n 10
```

This command will print out the last 10 lines of dmesg, which may give us a clue as to why the drive is not detected.

Jim

just info about the cpu, I'm afraid:
```
  $ dmesg | tail -n 10
[   73.490472] CPU0 attaching sched-domain:
[   73.490552]  domain 0: span 0-1 level CPU
[   73.490552]   groups: 0 1
[   73.490552]   domain 1: span 0-1 level NODE
[   73.490552]    groups: 0-1
[   73.490552] CPU1 attaching sched-domain:
[   73.490552]  domain 0: span 0-1 level CPU
[   73.490552]   groups: 1 0
[   73.490552]   domain 1: span 0-1 level NODE
[   73.490552]    groups: 0-1

```

I tried unplugging it and plugging it back in, but there was no change.

---

