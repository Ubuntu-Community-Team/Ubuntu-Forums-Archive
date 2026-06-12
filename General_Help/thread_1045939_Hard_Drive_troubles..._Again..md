---
title: "Hard Drive troubles... Again."
date: 2009-01-21
forum: General Help
---

### Post by Toadofsky on 2009-01-21
Okay, so about a few months ago, I needed help putting a Simple Tech 160 gigabyte hard drive to my Ubuntu (version 8.10), eventually I got it to run, and I've enjoyed it thus far.

Just a few hours ago, I UNPLUGGED it from the computer, to take to a friends house, to show him some videos (he runs Windows on his laptop). I plugged it in, showed him the videos, and that's all.

Now, I plug it back in, and it's giving me this error...

Unable to mount signature mini...

So here's what my "dmesg" says...

[61326.801177] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[61326.801218] usb usb1: root hub lost power or was reset
[61326.801236] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[61326.801241] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[61326.801280] usb usb2: root hub lost power or was reset
[61326.801305] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[61326.801310] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[61326.801350] usb usb3: root hub lost power or was reset
[61326.801373] uhci_hcd 0000:00:1d.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[61326.801378] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[61326.801418] usb usb4: root hub lost power or was reset
[61326.816017] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[61326.816023] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[61326.816097] pci 0000:00:1e.0: setting latency timer to 64
[61326.816136] ata_piix 0000:00:1f.1: restoring config space at offset 0x9 (was 0x0, writing 0x30000000)
[61326.816151] ata_piix 0000:00:1f.1: restoring config space at offset 0x1 (was 0x2880005, writing 0x2880007)
[61326.816161] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[61326.816166] ata_piix 0000:00:1f.1: setting latency timer to 64
[61326.816225] ata_piix 0000:00:1f.2: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[61326.816232] ata_piix 0000:00:1f.2: setting latency timer to 64
[61326.816458] Intel ICH 0000:00:1f.5: restoring config space at offset 0x1 (was 0x2900007, writing 0x2900003)
[61326.816476] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[61326.816485] Intel ICH 0000:00:1f.5: setting latency timer to 64
[61326.826160] NVRM: RmPowerManagement: 5
[61326.994303] ata2.01: ACPI cmd ef/03:42:00:00:00:b0 filtered out
[61326.994309] ata2.01: ACPI cmd ef/03:0c:00:00:00:b0 filtered out
[61327.121374] ata2.00: ACPI cmd ef/03:42:00:00:00:a0 filtered out
[61327.121379] ata2.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[61327.137296] ata2.00: configured for UDMA/33
[61327.153293] ata2.01: configured for UDMA/33
[61327.799892] pci 0000:02:0a.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[61327.812023] ohci1394 0000:02:0e.0: restoring config space at offset 0xf (was 0x4030100, writing 0x403010a)
[61327.812040] ohci1394 0000:02:0e.0: restoring config space at offset 0x5 (was 0x0, writing 0xfeaf8000)
[61327.812045] ohci1394 0000:02:0e.0: restoring config space at offset 0x4 (was 0x0, writing 0xfeaff000)
[61327.812051] ohci1394 0000:02:0e.0: restoring config space at offset 0x3 (was 0x0, writing 0x4004)
[61327.812058] ohci1394 0000:02:0e.0: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100116)
[61327.861692] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[feaff000-feaff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[61327.863166] serial 00:05: activated
[61327.864600] parport_pc 00:07: activated
[61328.672064] sd 0:0:0:0: [sda] Starting disk
[61331.865014] ata1: link is slow to respond, please be patient (ready=0)
[61332.981294] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
[61332.981297] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[61332.981442] ata1.00: ACPI cmd c6/00:10:00:00:00:a0 succeeded
[61333.005410] ata1.00: configured for UDMA/100
[61333.029407] ata1.00: configured for UDMA/100
[61333.029411] ata1: EH complete
[61333.051216] sd 0:0:0:0: [sda] 320173056 512-byte hardware sectors (163929 MB)
[61333.051270] sd 0:0:0:0: [sda] Write Protect is off
[61333.051274] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[61333.051339] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[61333.051402] sd 0:0:0:0: [sda] 320173056 512-byte hardware sectors (163929 MB)
[61333.051437] sd 0:0:0:0: [sda] Write Protect is off
[61333.051440] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[61333.051507] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[61333.356016] usb 2-2: reset low speed USB device using uhci_hcd and address 3
[61333.932014] usb 3-1: reset low speed USB device using uhci_hcd and address 3
[61334.704015] usb 4-1: reset low speed USB device using uhci_hcd and address 2
[61335.128015] usb 4-2: reset full speed USB device using uhci_hcd and address 3
[61335.287560] PM: resume devices took 8.484 seconds
[61335.287570] ------------[ cut here ]------------
[61335.287572] WARNING: at /build/buildd/linux-2.6.27/kernel/power/main.c:176 suspend_test_finish+0x74/0x80()
[61335.287575] Modules linked in: ipv6 af_packet binfmt_misc sco bridge stp bnep rfcomm l2cap bluetooth ppdev speedstep_lib cpufreq_powersave cpufreq_ondemand cpufreq_stats freq_table cpufreq_conservative cpufreq_userspace sbs sbshc container wmi pci_slot video output battery iptable_filter ip_tables x_tables ac sbp2 lp joydev snd_intel8x0 snd_ac97_codec pcspkr ac97_bus snd_pcm_oss evdev snd_mixer_oss snd_pcm psmouse serio_raw snd_seq_dummy cx8800 cx88xx ir_common i2c_algo_bit tveeprom videodev v4l1_compat compat_ioctl32 v4l2_common snd_seq_oss videobuf_dma_sg videobuf_core btcx_risc snd_seq_midi parport_pc parport snd_rawmidi nvidia(P) i2c_core snd_seq_midi_event snd_seq snd_timer snd_seq_device snd button soundcore snd_page_alloc iTCO_wdt iTCO_vendor_support intel_agp agpgart shpchp pci_hotplug ext3 jbd mbcache sd_mod crc_t10dif sr_mod cdrom sg pata_acpi ata_generic 8139cp usb_storage usbhid hid libusual ata_piix libata scsi_mod ohci1394 8139too mii dock ieee1394 ehci_hcd uhci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[61335.287660] Pid: 16229, comm: pm-suspend Tainted: P        W 2.6.27-9-generic #1
[61335.287664]  [<c037c4b6>] ? printk+0x1d/0x1f
[61335.287672]  [<c0131de9>] warn_on_slowpath+0x59/0x90
[61335.287678]  [<c014d255>] ? sched_clock_cpu+0xd5/0x170
[61335.287684]  [<c014c0af>] ? down_trylock+0x2f/0x40
[61335.287688]  [<c01324c2>] ? try_acquire_console_sem+0x12/0x40
[61335.287692]  [<c024e580>] ? kobject_put+0x20/0x50
[61335.287697]  [<c015d204>] suspend_test_finish+0x74/0x80
[61335.287701]  [<c015d2f6>] suspend_devices_and_enter+0xe6/0x190
[61335.287705]  [<c015d571>] enter_state+0xd1/0x100
[61335.287708]  [<c015d625>] state_store+0x85/0xd0
[61335.287711]  [<c015d5a0>] ? state_store+0x0/0xd0
[61335.287715]  [<c024e444>] kobj_attr_store+0x24/0x30
[61335.287718]  [<c01ff4c7>] sysfs_write_file+0x97/0x100
[61335.287722]  [<c01b24c0>] vfs_write+0xa0/0x110
[61335.287727]  [<c01ff430>] ? sysfs_write_file+0x0/0x100
[61335.287731]  [<c01b2602>] sys_write+0x42/0x70
[61335.287734]  [<c0103f7b>] sysenter_do_call+0x12/0x2f
[61335.287739]  [<c0370000>] ? netdev_exit+0x10/0x20
[61335.287744]  =======================
[61335.287746] ---[ end trace c2c0e0515114beaa ]---
[61335.287859] PM: Finishing wakeup.
[61335.287862] Restarting tasks ... done.
[61336.234987] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[61346.677093] eth0: no IPv6 routers present
[68705.712772] PM: Syncing filesystems ... done.
[68705.721035] PM: Preparing system for mem sleep
[68705.721044] Freezing user space processes ... (elapsed 0.21 seconds) done.
[68705.933790] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[68705.933946] PM: Entering mem sleep
[68705.933950] Suspending console(s) (use no_console_suspend to debug)
[68706.020035] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[68706.155713] sd 0:0:0:0: [sda] Stopping disk
[68706.269408] parport_pc 00:07: disabled
[68706.269767] serial 00:05: disabled
[68706.269861] ACPI handle has no context!
[68706.284087] ACPI handle has no context!
[68706.284103] NVRM: RmPowerManagement: 4
[68706.367273] Intel ICH 0000:00:1f.5: PCI INT B disabled
[68706.367443] ata_piix 0000:00:1f.2: PCI INT A disabled
[68706.367558] ata_piix 0000:00:1f.1: PCI INT A disabled
[68706.367657] ehci_hcd 0000:00:1d.7: PCI INT D disabled
[68706.380045] uhci_hcd 0000:00:1d.3: PCI INT A disabled
[68706.380075] uhci_hcd 0000:00:1d.2: PCI INT C disabled
[68706.380105] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[68706.380135] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[68706.380223] PM: suspend devices took 0.448 seconds
[68706.380273] ACPI: Preparing to enter system sleep state S3
[68706.380796] Disabling non-boot CPUs ...
[68706.484021] CPU 1 is now offline
[68706.484025] SMP alternatives: switching to UP code
[68706.500274] CPU0 attaching NULL sched-domain.
[68706.500279] CPU1 attaching NULL sched-domain.
[68706.500318] CPU0 attaching sched-domain:
[68706.500322]  domain 0: span 0 level CPU
[68706.500324]   groups: 0
[68706.500558] CPU1 is down
[68706.500558] Back to C!
[68706.500558] Force enabled HPET at resume
[68706.500558] Enabling non-boot CPUs ...
[68706.500558] SMP alternatives: switching to SMP code
[68706.517364] Booting processor 1/1 ip 6000
[68706.384955] Initializing CPU#1
[68706.384955] Calibrating delay using timer specific routine.. 6000.29 BogoMIPS (lpj=12000583)
[68706.384955] CPU: Trace cache: 12K uops, L1 D cache: 8K
[68706.384955] CPU: L2 cache: 512K
[68706.384955] CPU: Physical Processor ID: 0
[68706.608184] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 09
[68706.608205] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[68706.628287] CPU0 attaching NULL sched-domain.
[68706.632013] Switched to high resolution mode on CPU 1
[68706.636020] CPU0 attaching sched-domain:
[68706.636024]  domain 0: span 0-1 level SIBLING
[68706.636027]   groups: 0 1
[68706.636031]   domain 1: span 0-1 level CPU
[68706.636033]    groups: 0-1
[68706.636038] CPU1 attaching sched-domain:
[68706.636040]  domain 0: span 0-1 level SIBLING
[68706.636042]   groups: 1 0
[68706.636045]   domain 1: span 0-1 level CPU
[68706.636047]    groups: 0-1
[68706.636521] CPU1 is up
[68706.636526] ACPI: Waking up from system sleep state S3
[68706.637123] pm_op(): pci_pm_resume+0x0/0x80 returns -16
[68706.637133] PM: Device 0000:00:00.0 failed to resume: error -16
[68706.637166] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[68706.637171] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[68706.637213] usb usb1: root hub lost power or was reset
[68706.637230] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[68706.637235] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[68706.637275] usb usb2: root hub lost power or was reset
[68706.637300] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[68706.637305] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[68706.637344] usb usb3: root hub lost power or was reset
[68706.637368] uhci_hcd 0000:00:1d.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[68706.637373] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[68706.637412] usb usb4: root hub lost power or was reset
[68706.652018] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[68706.652023] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[68706.652097] pci 0000:00:1e.0: setting latency timer to 64
[68706.652136] ata_piix 0000:00:1f.1: restoring config space at offset 0x9 (was 0x0, writing 0x30000000)
[68706.652151] ata_piix 0000:00:1f.1: restoring config space at offset 0x1 (was 0x2880005, writing 0x2880007)
[68706.652161] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[68706.652166] ata_piix 0000:00:1f.1: setting latency timer to 64
[68706.652277] ata_piix 0000:00:1f.2: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[68706.652285] ata_piix 0000:00:1f.2: setting latency timer to 64
[68706.652509] Intel ICH 0000:00:1f.5: restoring config space at offset 0x1 (was 0x2900007, writing 0x2900003)
[68706.652528] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[68706.652537] Intel ICH 0000:00:1f.5: setting latency timer to 64
[68706.662171] NVRM: RmPowerManagement: 5
[68706.830286] ata2.01: ACPI cmd ef/03:42:00:00:00:b0 filtered out
[68706.830291] ata2.01: ACPI cmd ef/03:0c:00:00:00:b0 filtered out
[68706.957368] ata2.00: ACPI cmd ef/03:42:00:00:00:a0 filtered out
[68706.957373] ata2.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[68706.973294] ata2.00: configured for UDMA/33
[68706.989298] ata2.01: configured for UDMA/33
[68707.634656] pci 0000:02:0a.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[68707.648024] ohci1394 0000:02:0e.0: restoring config space at offset 0xf (was 0x4030100, writing 0x403010a)
[68707.648040] ohci1394 0000:02:0e.0: restoring config space at offset 0x5 (was 0x0, writing 0xfeaf8000)
[68707.648046] ohci1394 0000:02:0e.0: restoring config space at offset 0x4 (was 0x0, writing 0xfeaff000)
[68707.648051] ohci1394 0000:02:0e.0: restoring config space at offset 0x3 (was 0x0, writing 0x4004)
[68707.648057] ohci1394 0000:02:0e.0: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100116)
[68707.697689] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[feaff000-feaff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[68707.699074] serial 00:05: activated
[68707.700413] parport_pc 00:07: activated
[68708.508059] sd 0:0:0:0: [sda] Starting disk
[68711.700020] ata1: link is slow to respond, please be patient (ready=0)
[68712.816294] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
[68712.816297] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[68712.816442] ata1.00: ACPI cmd c6/00:10:00:00:00:a0 succeeded
[68712.841414] ata1.00: configured for UDMA/100
[68712.865408] ata1.00: configured for UDMA/100
[68712.865412] ata1: EH complete
[68712.881325] sd 0:0:0:0: [sda] 320173056 512-byte hardware sectors (163929 MB)
[68712.881384] sd 0:0:0:0: [sda] Write Protect is off
[68712.881388] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[68712.881441] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[68712.881485] sd 0:0:0:0: [sda] 320173056 512-byte hardware sectors (163929 MB)
[68712.881510] sd 0:0:0:0: [sda] Write Protect is off
[68712.881513] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[68712.881556] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[68713.188015] usb 2-2: reset low speed USB device using uhci_hcd and address 3
[68713.764015] usb 3-1: reset low speed USB device using uhci_hcd and address 3
[68714.332014] usb 4-1: reset low speed USB device using uhci_hcd and address 2
[68714.756014] usb 4-2: reset full speed USB device using uhci_hcd and address 3
[68714.915592] PM: resume devices took 8.276 seconds
[68714.915603] ------------[ cut here ]------------
[68714.915605] WARNING: at /build/buildd/linux-2.6.27/kernel/power/main.c:176 suspend_test_finish+0x74/0x80()
[68714.915608] Modules linked in: ipv6 af_packet binfmt_misc sco bridge stp bnep rfcomm l2cap bluetooth ppdev speedstep_lib cpufreq_powersave cpufreq_ondemand cpufreq_stats freq_table cpufreq_conservative cpufreq_userspace sbs sbshc container wmi pci_slot video output battery iptable_filter ip_tables x_tables ac sbp2 lp joydev snd_intel8x0 snd_ac97_codec pcspkr ac97_bus snd_pcm_oss evdev snd_mixer_oss snd_pcm psmouse serio_raw snd_seq_dummy cx8800 cx88xx ir_common i2c_algo_bit tveeprom videodev v4l1_compat compat_ioctl32 v4l2_common snd_seq_oss videobuf_dma_sg videobuf_core btcx_risc snd_seq_midi parport_pc parport snd_rawmidi nvidia(P) i2c_core snd_seq_midi_event snd_seq snd_timer snd_seq_device snd button soundcore snd_page_alloc iTCO_wdt iTCO_vendor_support intel_agp agpgart shpchp pci_hotplug ext3 jbd mbcache sd_mod crc_t10dif sr_mod cdrom sg pata_acpi ata_generic 8139cp usb_storage usbhid hid libusual ata_piix libata scsi_mod ohci1394 8139too mii dock ieee1394 ehci_hcd uhci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[68714.915688] Pid: 17371, comm: pm-suspend Tainted: P        W 2.6.27-9-generic #1
[68714.915692]  [<c037c4b6>] ? printk+0x1d/0x1f
[68714.915700]  [<c0131de9>] warn_on_slowpath+0x59/0x90
[68714.915707]  [<c014d255>] ? sched_clock_cpu+0xd5/0x170
[68714.915712]  [<c014c0af>] ? down_trylock+0x2f/0x40
[68714.915716]  [<c01324c2>] ? try_acquire_console_sem+0x12/0x40
[68714.915721]  [<c024e580>] ? kobject_put+0x20/0x50
[68714.915726]  [<c015d204>] suspend_test_finish+0x74/0x80
[68714.915730]  [<c015d2f6>] suspend_devices_and_enter+0xe6/0x190
[68714.915734]  [<c015d571>] enter_state+0xd1/0x100
[68714.915737]  [<c015d625>] state_store+0x85/0xd0
[68714.915740]  [<c015d5a0>] ? state_store+0x0/0xd0
[68714.915744]  [<c024e444>] kobj_attr_store+0x24/0x30
[68714.915747]  [<c01ff4c7>] sysfs_write_file+0x97/0x100
[68714.915752]  [<c01b24c0>] vfs_write+0xa0/0x110
[68714.915756]  [<c01ff430>] ? sysfs_write_file+0x0/0x100
[68714.915759]  [<c01b2602>] sys_write+0x42/0x70
[68714.915763]  [<c0103f7b>] sysenter_do_call+0x12/0x2f
[68714.915767]  [<c0370000>] ? netdev_exit+0x10/0x20
[68714.915771]  =======================
[68714.915774] ---[ end trace c2c0e0515114beaa ]---
[68714.915887] PM: Finishing wakeup.
[68714.915889] Restarting tasks ... done.
[68715.807149] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[68726.600019] eth0: no IPv6 routers present
[69749.332268] hub 5-0:1.0: unable to enumerate USB device on port 6
[69759.441531] usb 5-6: new high speed USB device using ehci_hcd and address 8
[69759.575169] usb 5-6: configuration #1 chosen from 1 choice
[69759.579661] scsi6 : SCSI emulation for USB Mass Storage devices
[69759.580831] usb-storage: device found at 8
[69759.580841] usb-storage: waiting for device to settle before scanning
[69764.577310] usb-storage: device scan complete
[69764.578230] scsi 6:0:0:0: Direct-Access     SanDisk  Sansa Clip 4GB   v02. PQ: 0 ANSI: 0
[69764.585060] sd 6:0:0:0: [sdg] 7683072 512-byte hardware sectors (3934 MB)
[69764.586692] sd 6:0:0:0: [sdg] Write Protect is off
[69764.586699] sd 6:0:0:0: [sdg] Mode Sense: 04 00 00 00
[69764.586705] sd 6:0:0:0: [sdg] Assuming drive cache: write through
[69764.590026] sd 6:0:0:0: [sdg] 7683072 512-byte hardware sectors (3934 MB)
[69764.590533] sd 6:0:0:0: [sdg] Write Protect is off
[69764.590540] sd 6:0:0:0: [sdg] Mode Sense: 04 00 00 00
[69764.590545] sd 6:0:0:0: [sdg] Assuming drive cache: write through
[69764.590557]  sdg:
[69764.603697] sd 6:0:0:0: [sdg] Attached SCSI removable disk
[69764.605334] sd 6:0:0:0: Attached scsi generic sg8 type 0
[70470.730704] usb 5-1: USB disconnect, address 2
[73482.339341] PM: Syncing filesystems ... done.
[73482.339851] PM: Preparing system for mem sleep
[73482.339859] Freezing user space processes ... (elapsed 0.02 seconds) done.
[73482.368456] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[73482.368606] PM: Entering mem sleep
[73482.368611] Suspending console(s) (use no_console_suspend to debug)
[73482.456037] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[73482.656047] sd 0:0:0:0: [sda] Stopping disk
[73482.771794] parport_pc 00:07: disabled
[73482.772162] serial 00:05: disabled
[73482.772257] ACPI handle has no context!
[73482.788079] ACPI handle has no context!
[73482.788094] NVRM: RmPowerManagement: 4
[73482.871321] Intel ICH 0000:00:1f.5: PCI INT B disabled
[73482.871497] ata_piix 0000:00:1f.2: PCI INT A disabled
[73482.871616] ata_piix 0000:00:1f.1: PCI INT A disabled
[73482.871716] ehci_hcd 0000:00:1d.7: PCI INT D disabled
[73482.884050] uhci_hcd 0000:00:1d.3: PCI INT A disabled
[73482.884080] uhci_hcd 0000:00:1d.2: PCI INT C disabled
[73482.884110] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[73482.884140] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[73482.884229] PM: suspend devices took 0.516 seconds
[73482.884278] ACPI: Preparing to enter system sleep state S3
[73482.884806] Disabling non-boot CPUs ...
[73482.988022] CPU 1 is now offline
[73482.988026] SMP alternatives: switching to UP code
[73483.003873] CPU0 attaching NULL sched-domain.
[73483.003877] CPU1 attaching NULL sched-domain.
[73483.003919] CPU0 attaching sched-domain:
[73483.003922]  domain 0: span 0 level CPU
[73483.003925]   groups: 0
[73483.004178] CPU1 is down
[73483.004178] Back to C!
[73483.004178] Force enabled HPET at resume
[73483.004178] Enabling non-boot CPUs ...
[73483.004178] SMP alternatives: switching to SMP code
[73483.020666] Booting processor 1/1 ip 6000
[73482.888972] Initializing CPU#1
[73482.888972] Calibrating delay using timer specific routine.. 6000.18 BogoMIPS (lpj=12000365)
[73482.888972] CPU: Trace cache: 12K uops, L1 D cache: 8K
[73482.888972] CPU: L2 cache: 512K
[73482.888972] CPU: Physical Processor ID: 0
[73483.108181] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 09
[73483.108202] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[73483.128317] CPU0 attaching NULL sched-domain.
[73483.132013] Switched to high resolution mode on CPU 1
[73483.136020] CPU0 attaching sched-domain:
[73483.136023]  domain 0: span 0-1 level SIBLING
[73483.136026]   groups: 0 1
[73483.136030]   domain 1: span 0-1 level CPU
[73483.136032]    groups: 0-1
[73483.136037] CPU1 attaching sched-domain:
[73483.136039]  domain 0: span 0-1 level SIBLING
[73483.136041]   groups: 1 0
[73483.136044]   domain 1: span 0-1 level CPU
[73483.136046]    groups: 0-1
[73483.136520] CPU1 is up
[73483.136525] ACPI: Waking up from system sleep state S3
[73483.137119] pm_op(): pci_pm_resume+0x0/0x80 returns -16
[73483.137129] PM: Device 0000:00:00.0 failed to resume: error -16
[73483.137163] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[73483.137168] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[73483.137210] usb usb1: root hub lost power or was reset
[73483.137227] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[73483.137232] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[73483.137271] usb usb2: root hub lost power or was reset
[73483.137296] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[73483.137301] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[73483.137340] usb usb3: root hub lost power or was reset
[73483.137364] uhci_hcd 0000:00:1d.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[73483.137369] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[73483.137408] usb usb4: root hub lost power or was reset
[73483.152018] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[73483.152023] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[73483.152097] pci 0000:00:1e.0: setting latency timer to 64
[73483.152136] ata_piix 0000:00:1f.1: restoring config space at offset 0x9 (was 0x0, writing 0x30000000)
[73483.152150] ata_piix 0000:00:1f.1: restoring config space at offset 0x1 (was 0x2880005, writing 0x2880007)
[73483.152160] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[73483.152165] ata_piix 0000:00:1f.1: setting latency timer to 64
[73483.152222] ata_piix 0000:00:1f.2: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[73483.152230] ata_piix 0000:00:1f.2: setting latency timer to 64
[73483.152455] Intel ICH 0000:00:1f.5: restoring config space at offset 0x1 (was 0x2900007, writing 0x2900003)
[73483.152472] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[73483.152480] Intel ICH 0000:00:1f.5: setting latency timer to 64
[73483.162155] NVRM: RmPowerManagement: 5
[73483.330318] ata2.01: ACPI cmd ef/03:42:00:00:00:b0 filtered out
[73483.330323] ata2.01: ACPI cmd ef/03:0c:00:00:00:b0 filtered out
[73483.457369] ata2.00: ACPI cmd ef/03:42:00:00:00:a0 filtered out
[73483.457374] ata2.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[73483.473295] ata2.00: configured for UDMA/33
[73483.489305] ata2.01: configured for UDMA/33
[73484.137149] pci 0000:02:0a.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[73484.152022] ohci1394 0000:02:0e.0: restoring config space at offset 0xf (was 0x4030100, writing 0x403010a)
[73484.152039] ohci1394 0000:02:0e.0: restoring config space at offset 0x5 (was 0x0, writing 0xfeaf8000)
[73484.152044] ohci1394 0000:02:0e.0: restoring config space at offset 0x4 (was 0x0, writing 0xfeaff000)
[73484.152049] ohci1394 0000:02:0e.0: restoring config space at offset 0x3 (was 0x0, writing 0x4004)
[73484.152056] ohci1394 0000:02:0e.0: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100116)
[73484.201689] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[feaff000-feaff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[73484.203049] serial 00:05: activated
[73484.204377] parport_pc 00:07: activated
[73485.012051] sd 0:0:0:0: [sda] Starting disk
[73488.200020] ata1: link is slow to respond, please be patient (ready=0)
[73489.316294] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
[73489.316297] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[73489.316445] ata1.00: ACPI cmd c6/00:10:00:00:00:a0 succeeded
[73489.341408] ata1.00: configured for UDMA/100
[73489.365407] ata1.00: configured for UDMA/100
[73489.365411] ata1: EH complete
[73489.387352] sd 0:0:0:0: [sda] 320173056 512-byte hardware sectors (163929 MB)
[73489.387405] sd 0:0:0:0: [sda] Write Protect is off
[73489.387409] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[73489.387472] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[73489.387517] sd 0:0:0:0: [sda] 320173056 512-byte hardware sectors (163929 MB)
[73489.387541] sd 0:0:0:0: [sda] Write Protect is off
[73489.387543] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[73489.387586] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[73489.644016] usb 2-2: reset low speed USB device using uhci_hcd and address 3
[73490.220014] usb 3-1: reset low speed USB device using uhci_hcd and address 3
[73490.788014] usb 4-1: reset low speed USB device using uhci_hcd and address 2
[73491.212022] usb 4-2: reset full speed USB device using uhci_hcd and address 3
[73491.420836] PM: resume devices took 8.284 seconds
[73491.420846] ------------[ cut here ]------------
[73491.420849] WARNING: at /build/buildd/linux-2.6.27/kernel/power/main.c:176 suspend_test_finish+0x74/0x80()
[73491.420851] Modules linked in: nls_iso8859_1 nls_cp437 vfat fat ipv6 af_packet binfmt_misc sco bridge stp bnep rfcomm l2cap bluetooth ppdev speedstep_lib cpufreq_powersave cpufreq_ondemand cpufreq_stats freq_table cpufreq_conservative cpufreq_userspace sbs sbshc container wmi pci_slot video output battery iptable_filter ip_tables x_tables ac sbp2 lp joydev snd_intel8x0 snd_ac97_codec pcspkr ac97_bus snd_pcm_oss evdev snd_mixer_oss snd_pcm psmouse serio_raw snd_seq_dummy cx8800 cx88xx ir_common i2c_algo_bit tveeprom videodev v4l1_compat compat_ioctl32 v4l2_common snd_seq_oss videobuf_dma_sg videobuf_core btcx_risc snd_seq_midi parport_pc parport snd_rawmidi nvidia(P) i2c_core snd_seq_midi_event snd_seq snd_timer snd_seq_device snd button soundcore snd_page_alloc iTCO_wdt iTCO_vendor_support intel_agp agpgart shpchp pci_hotplug ext3 jbd mbcache sd_mod crc_t10dif sr_mod cdrom sg pata_acpi ata_generic 8139cp usb_storage usbhid hid libusual ata_piix libata scsi_mod ohci1394 8139too mii dock ieee1394 ehci_hcd uhci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[73491.420939] Pid: 18182, comm: pm-suspend Tainted: P        W 2.6.27-9-generic #1
[73491.420942]  [<c037c4b6>] ? printk+0x1d/0x1f
[73491.420950]  [<c0131de9>] warn_on_slowpath+0x59/0x90
[73491.420957]  [<c014d255>] ? sched_clock_cpu+0xd5/0x170
[73491.420962]  [<c014c0af>] ? down_trylock+0x2f/0x40
[73491.420966]  [<c01324c2>] ? try_acquire_console_sem+0x12/0x40
[73491.420971]  [<c024e580>] ? kobject_put+0x20/0x50
[73491.420976]  [<c015d204>] suspend_test_finish+0x74/0x80
[73491.420980]  [<c015d2f6>] suspend_devices_and_enter+0xe6/0x190
[73491.420984]  [<c015d571>] enter_state+0xd1/0x100
[73491.420987]  [<c015d625>] state_store+0x85/0xd0
[73491.420990]  [<c015d5a0>] ? state_store+0x0/0xd0
[73491.420994]  [<c024e444>] kobj_attr_store+0x24/0x30
[73491.420997]  [<c01ff4c7>] sysfs_write_file+0x97/0x100
[73491.421001]  [<c01b24c0>] vfs_write+0xa0/0x110
[73491.421006]  [<c01ff430>] ? sysfs_write_file+0x0/0x100
[73491.421009]  [<c01b2602>] sys_write+0x42/0x70
[73491.421013]  [<c0103f7b>] sysenter_do_call+0x12/0x2f
[73491.421017]  [<c0370000>] ? netdev_exit+0x10/0x20
[73491.421021]  =======================
[73491.421023] ---[ end trace c2c0e0515114beaa ]---
[73491.421135] PM: Finishing wakeup.
[73491.421138] Restarting tasks ... done.
[73492.794990] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[73503.624015] eth0: no IPv6 routers present
[73523.228046] usb 5-1: new high speed USB device using ehci_hcd and address 9
[73523.376494] usb 5-1: configuration #1 chosen from 1 choice
[73523.377575] scsi7 : SCSI emulation for USB Mass Storage devices
[73523.380183] usb-storage: device found at 9
[73523.380198] usb-storage: waiting for device to settle before scanning
[73528.377184] usb-storage: device scan complete
[73528.378031] scsi 7:0:0:0: Direct-Access     WDC WD16 00BEVS-00RST0    04.0 PQ: 0 ANSI: 0
[73528.381541] sd 7:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[73528.382407] sd 7:0:0:0: [sdb] Write Protect is off
[73528.382415] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[73528.382421] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[73528.383144] sd 7:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[73528.384002] sd 7:0:0:0: [sdb] Write Protect is off
[73528.384017] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[73528.384022] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[73528.384034]  sdb: sdb1
[73528.440748] sd 7:0:0:0: [sdb] Attached SCSI disk
[73528.441630] sd 7:0:0:0: Attached scsi generic sg3 type 0

Can I get this thing back up and running on my Ubuntu without losing my files? And, how can I unplug this should I want to take this to a friends house? And then get it back running?

Thanks.

---

### Post by sam1948 on 2009-01-21
is it a usb disk?
it seems like the usb hardware is not so good
try another usb in the computer or even on another computer
besides that u might want to reconnect the disk to the windows machine and turn off the computer before removing it
good luck

---

### Post by Yashiro on 2009-01-21
If you open a Nautilus filebrowser Window and select Go menu, Computer, is the USB drive not visible?

---

### Post by Toadofsky on 2009-01-21
Well, at my places directory, at removable media, I can see it there. But it won't allow me to access it.

And no, it doesn't list it at the Computer file browser window

---

### Post by jerome1232 on 2009-01-21
What's the exact error when you attempt to mount it

```
sudo mount /dev/sdb1 /mnt
```


My guess is that you simply unplugged it from the windows computer, which leaves the log file dirty on ntfs drives (easy fix). But let's see the error before jumping to conclusions :)

---

### Post by Toadofsky on 2009-01-21
Here's my error...

$LogFile indicates unclean shutdown (0, 1)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /mnt -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /mnt ntfs-3g force 0 0


I'm about to lose everything I had on it, aren't I?

---

### Post by jerome1232 on 2009-01-21
To the contrary this is an easy fix. This just means what I thought, next time before you unplug the drive be sure to select "safely remove hardware" in windows before you just remove it.

Basically you just need to clear the log file that's telling ubuntu the disc was rudely removed last time it was used.

You will need ntfsprogs
```
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sdb1
```

---

### Post by Toadofsky on 2009-01-21
That did it! Thanks guys! I REALLY appreciate all the help. I'll be sure to be a little more active here. Especially on learning things here.

---

