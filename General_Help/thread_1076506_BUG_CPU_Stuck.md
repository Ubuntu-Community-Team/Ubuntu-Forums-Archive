---
title: "BUG: CPU Stuck"
date: 2009-02-21
forum: General Help
---

### Post by kinsei on 2009-02-21
Hello-
I am building a new system and on a default install of Ubuntu 8.10 am receiving the following messages each time I try to complete a large file transfer.  The entire system freezes and I have to perform a hardware reset each time to reboot the system.  I have seen others posting the same problem around the web but don't see any fixes for it  yet.

Can anyone help me to diagnose what is going on or to figure out a workaround?

My machine is an EVGA X58 SLI Mobo w/ 12 GB RAM, EVGA 9800 Video Card, Adaptec 5805 RAID Controller, Intel Gigabit e1000 NIC.

I have experienced issues like this before the Adaptec card was installed.  It seems to be related to the either the Mobo, the processor, or the kernel I am guessing.

Thanks in advance.
Tim



Feb 20 07:13:07 ROCK kernel: [29226.126910] general protection fault: 0000 [1] SMP
Feb 20 07:13:07 ROCK kernel: [29226.126914] CPU 4
Feb 20 07:13:07 ROCK kernel: [29226.126915] Modules linked in: binfmt_misc rfcomm sco bridge stp bnep l2cap bluetooth ppdev acpi_cpufreq cpufreq_powersave cpufreq_ondemand cpufreq_stats cpufreq_conservative freq_table cpufreq_userspace sbs sbshc container video output pci_slot battery ipv6 iptable_filter ip_tables x_tables ac sbp2 parport_pc lp parport snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore nvidia(P) pcspkr evdev snd_page_alloc i2c_core wmi shpchp button pci_hotplug ext3 jbd mbcache sr_mod cdrom usb_storage usbhid hid libusual ata_piix pata_acpi sd_mod crc_t10dif sg ata_generic ohci1394 ehci_hcd libata e1000 ieee1394 aacraid dock uhci_hcd scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
Feb 20 07:13:07 ROCK kernel: [29226.126953] Pid: 8387, comm: kjournald Tainted: P          2.6.27-11-generic #1
Feb 20 07:13:07 ROCK kernel: [29226.126955] RIP: 0010:[<ffffffffa01f3be2>]  [<ffffffffa01f3be2>] __journal_temp_unlink_buffer+0xa2/0x1a0 [jbd]
Feb 20 07:13:07 ROCK kernel: [29226.126962] RSP: 0018:ffff880352073d10  EFLAGS: 00010206
Feb 20 07:13:07 ROCK kernel: [29226.126963] RAX: fffb880260308060 RBX: ffff88021b015a10 RCX: 0000000000000004
Feb 20 07:13:07 ROCK kernel: [29226.126965] RDX: ffff88027e1dc7e0 RSI: ffff8801d1c28338 RDI: ffff880357002554
Feb 20 07:13:07 ROCK kernel: [29226.126966] RBP: ffff880352073d40 R08: 0000000000000000 R09: ffff880028103000
Feb 20 07:13:07 ROCK kernel: [29226.126967] R10: 0000000000000002 R11: 0000000000000644 R12: 0000000000000200
Feb 20 07:13:07 ROCK kernel: [29226.126968] R13: ffff88021b015a10 R14: ffff8801d1c28300 R15: ffff880260308000
Feb 20 07:13:07 ROCK kernel: [29226.126970] FS:  0000000000000000(0000) GS:ffff88035e46f400(0000) knlGS:0000000000000000
Feb 20 07:13:07 ROCK kernel: [29226.126972] CS:  0010 DS: 0018 ES: 0018 CR0: 000000008005003b
Feb 20 07:13:07 ROCK kernel: [29226.126973] CR2: 00007f0cb80d5028 CR3: 000000034ed6f000 CR4: 00000000000006e0
Feb 20 07:13:07 ROCK kernel: [29226.126974] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Feb 20 07:13:07 ROCK kernel: [29226.126976] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Feb 20 07:13:07 ROCK kernel: [29226.126977] Process kjournald (pid: 8387, threadinfo ffff880352072000, task ffff8803578e59c0)
Feb 20 07:13:07 ROCK kernel: [29226.126978] Stack:  ffff880352073d40 ffff880260308000 0000000000000200 ffff88021b015a10
Feb 20 07:13:07 ROCK kernel: [29226.126982]  ffff880260308000 0000000000000020 ffff880352073d60 ffffffffa01f3cf6
Feb 20 07:13:07 ROCK kernel: [29226.126984]  0000000000000010 0000000000000000 ffff880352073dd0 ffffffffa01f58e8
Feb 20 07:13:07 ROCK kernel: [29226.126986] Call Trace:
Feb 20 07:13:07 ROCK kernel: [29226.126991]  [<ffffffffa01f3cf6>] __journal_unfile_buffer+0x16/0x30 [jbd]
Feb 20 07:13:07 ROCK kernel: [29226.126995]  [<ffffffffa01f58e8>] journal_submit_data_buffers+0x1d8/0x350 [jbd]
Feb 20 07:13:07 ROCK kernel: [29226.126999]  [<ffffffffa01f5cc4>] journal_commit_transaction+0x264/0xd00 [jbd]
Feb 20 07:13:07 ROCK kernel: [29226.127003]  [<ffffffff8025a85b>] ? lock_timer_base+0x3b/0x70
Feb 20 07:13:07 ROCK kernel: [29226.127006]  [<ffffffff80267060>] ? autoremove_wake_function+0x0/0x40
Feb 20 07:13:07 ROCK kernel: [29226.127008]  [<ffffffff8025a8ef>] ? try_to_del_timer_sync+0x5f/0x70
Feb 20 07:13:07 ROCK kernel: [29226.127012]  [<ffffffffa01f9ed9>] kjournald+0xe9/0x250 [jbd]
Feb 20 07:13:07 ROCK kernel: [29226.127014]  [<ffffffff80267060>] ? autoremove_wake_function+0x0/0x40
Feb 20 07:13:07 ROCK kernel: [29226.127018]  [<ffffffffa01f9df0>] ? kjournald+0x0/0x250 [jbd]
Feb 20 07:13:07 ROCK kernel: [29226.127019]  [<ffffffff80266c2e>] kthread+0x4e/0x90
Feb 20 07:13:07 ROCK kernel: [29226.127022]  [<ffffffff80213c99>] child_rip+0xa/0x11
Feb 20 07:13:07 ROCK kernel: [29226.127023]  [<ffffffff80266be0>] ? kthread+0x0/0x90
Feb 20 07:13:07 ROCK kernel: [29226.127025]  [<ffffffff80213c8f>] ? child_rip+0x0/0x11
Feb 20 07:13:07 ROCK kernel: [29226.127026]
Feb 20 07:13:07 ROCK kernel: [29226.127026]
Feb 20 07:13:07 ROCK kernel: [29226.127027] Code: 00 00 31 f6 83 f8 08 76 50 4c 3b 3e 0f 1f 44 00 00 74 66 49 8b 57 40 49 8b 47 38 41 c7 47 0c 00 00 00 00 48 89 42 38 49 8b 47 38 <48> 89 50 40 f0 0f ba 33 14 19 c0 85 c0 74 ab 48 89 df e8 17 12
Feb 20 07:13:07 ROCK kernel: [29226.127045] RIP  [<ffffffffa01f3be2>] __journal_temp_unlink_buffer+0xa2/0x1a0 [jbd]
Feb 20 07:13:07 ROCK kernel: [29226.127050]  RSP <ffff880352073d10>
Feb 20 07:13:07 ROCK kernel: [29226.127055] ---[ end trace db2641e1e4091235 ]---
Feb 20 07:14:12 ROCK kernel: [29290.605744] BUG: soft lockup - CPU#7 stuck for 61s! [nautilus:20306]
Feb 20 07:14:12 ROCK kernel: [29290.605747] Modules linked in: binfmt_misc rfcomm sco bridge stp bnep l2cap bluetooth ppdev acpi_cpufreq cpufreq_powersave cpufreq_ondemand cpufreq_stats cpufreq_conservative freq_table cpufreq_userspace sbs sbshc container video output pci_slot battery ipv6 iptable_filter ip_tables x_tables ac sbp2 parport_pc lp parport snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore nvidia(P) pcspkr evdev snd_page_alloc i2c_core wmi shpchp button pci_hotplug ext3 jbd mbcache sr_mod cdrom usb_storage usbhid hid libusual ata_piix pata_acpi sd_mod crc_t10dif sg ata_generic ohci1394 ehci_hcd libata e1000 ieee1394 aacraid dock uhci_hcd scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
Feb 20 07:14:12 ROCK kernel: [29290.605752] CPU 7:
Feb 20 07:14:12 ROCK kernel: [29290.605752] Modules linked in: binfmt_misc rfcomm sco bridge stp bnep l2cap bluetooth ppdev acpi_cpufreq cpufreq_powersave cpufreq_ondemand cpufreq_stats cpufreq_conservative freq_table cpufreq_userspace sbs sbshc container video output pci_slot battery ipv6 iptable_filter ip_tables x_tables ac sbp2 parport_pc lp parport snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore nvidia(P) pcspkr evdev snd_page_alloc i2c_core wmi shpchp button pci_hotplug ext3 jbd mbcache sr_mod cdrom usb_storage usbhid hid libusual ata_piix pata_acpi sd_mod crc_t10dif sg ata_generic ohci1394 ehci_hcd libata e1000 ieee1394 aacraid dock uhci_hcd scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
Feb 20 07:14:12 ROCK kernel: [29290.605752] Pid: 20306, comm: nautilus Tainted: P      D   2.6.27-11-generic #1
Feb 20 07:14:12 ROCK kernel: [29290.605752] RIP: 0010:[<ffffffff8022d542>]  [<ffffffff8022d542>] __ticket_spin_lock+0x12/0x20
Feb 20 07:14:12 ROCK kernel: [29290.605752] RSP: 0018:ffff88022a80ba58  EFLAGS: 00000297
Feb 20 07:14:12 ROCK kernel: [29290.605752] RAX: 0000000000009998 RBX: ffff88022a80ba58 RCX: 0000000000000000
Feb 20 07:14:12 ROCK kernel: [29290.605752] RDX: 0000000000000000 RSI: ffff880050f84d20 RDI: ffff880357002554
Feb 20 07:14:12 ROCK kernel: [29290.605752] RBP: ffff88022a80b9e8 R08: 0000000000000000 R09: ffffffffa0209b50
Feb 20 07:14:12 ROCK kernel: [29290.605752] R10: 0000000000000037 R11: 0000000000000000 R12: 0000000000000007
Feb 20 07:14:12 ROCK kernel: [29290.605752] R13: 0000000000000001 R14: 0000000000000001 R15: ffff8800280b14a0
Feb 20 07:14:12 ROCK kernel: [29290.605752] FS:  0000000040c6b950(0063) GS:ffff88035e46fe80(0000) knlGS:0000000000000000
Feb 20 07:14:12 ROCK kernel: [29290.605752] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Feb 20 07:14:12 ROCK kernel: [29290.605752] CR2: 00007f0ccaf92000 CR3: 0000000359ce3000 CR4: 00000000000006e0
Feb 20 07:14:12 ROCK kernel: [29290.605752] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Feb 20 07:14:12 ROCK kernel: [29290.605752] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Feb 20 07:14:12 ROCK kernel: [29290.605752]
Feb 20 07:14:12 ROCK kernel: [29290.605752] Call Trace:
Feb 20 07:14:12 ROCK kernel: [29290.605752]  [<ffffffff8050367e>] ? _spin_lock+0xe/0x20
Feb 20 07:14:12 ROCK kernel: [29290.605752]  [<ffffffffa01f49cc>] ? journal_dirty_data+0x9c/0x240 [jbd]
Feb 20 07:14:12 ROCK kernel: [29290.605752]  [<ffffffffa0209b74>] ? ext3_journal_dirty_data+0x24/0x60 [ext3]
Feb 20 07:14:12 ROCK kernel: [29290.605752]  [<ffffffffa020a432>] ? walk_page_buffers+0x52/0xc0 [ext3]
Feb 20 07:14:12 ROCK kernel: [29290.605752]  [<ffffffffa0209b50>] ? ext3_journal_dirty_data+0x0/0x60 [ext3]
Feb 20 07:14:12 ROCK kernel: [29290.605752]  [<ffffffffa020a8c7>] ? ext3_ordered_write_end+0x77/0x160 [ext3]
Feb 20 07:14:12 ROCK kernel: [29290.605752]  [<ffffffff802ab92f>] ? generic_perform_write+0x11f/0x1c0
Feb 20 07:14:12 ROCK kernel: [29290.605752]  [<ffffffffa021c24b>] ? ext3_xattr_security_get+0x2b/0x30 [ext3]
Feb 20 07:14:12 ROCK kernel: [29290.605752]  [<ffffffffa021c24b>] ? ext3_xattr_security_get+0x2b/0x30 [ext3]
Feb 20 07:14:12 ROCK kernel: [29290.605752]  [<ffffffff802ad632>] ? generic_file_buffered_write+0x92/0x170
Feb 20 07:14:12 ROCK kernel: [29290.605752]  [<ffffffff802ae951>] ? __generic_file_aio_write_nolock+0x261/0x470
Feb 20 07:14:12 ROCK kernel: [29290.605752]  [<ffffffff802aec6c>] ? generic_file_aio_write+0x6c/0xd0
Feb 20 07:14:12 ROCK kernel: [29290.605752]  [<ffffffffa0207ccb>] ? ext3_file_write+0x2b/0xd0 [ext3]
Feb 20 07:14:12 ROCK kernel: [29290.605752]  [<ffffffff802e9b19>] ? do_sync_write+0xf9/0x140
Feb 20 07:14:12 ROCK kernel: [29290.605752]  [<ffffffff80267060>] ? autoremove_wake_function+0x0/0x40
Feb 20 07:14:12 ROCK kernel: [29290.605752]  [<ffffffff803873a1>] ? aa_file_permission+0x21/0xf0
Feb 20 07:14:12 ROCK kernel: [29290.605752]  [<ffffffff803874c8>] ? apparmor_file_permission+0x28/0x30
Feb 20 07:14:12 ROCK kernel: [29290.605752]  [<ffffffff80361f76>] ? security_file_permission+0x16/0x20
Feb 20 07:14:12 ROCK kernel: [29290.605752]  [<ffffffff802ea1db>] ? vfs_write+0xcb/0x130
Feb 20 07:14:12 ROCK kernel: [29290.605752]  [<ffffffff802ea335>] ? sys_write+0x55/0x90
Feb 20 07:14:12 ROCK kernel: [29290.605752]  [<ffffffff8021285a>] ? system_call_fastpath+0x16/0x1b
Feb 20 07:14:12 ROCK kernel: [29290.605752]
Feb 20 07:14:25 ROCK kernel: [29304.564994] BUG: soft lockup - CPU#4 stuck for 61s! [pdflush:20553]
Feb 20 07:14:25 ROCK kernel: [29304.564998] Modules linked in: binfmt_misc rfcomm sco bridge stp bnep l2cap bluetooth ppdev acpi_cpufreq cpufreq_powersave cpufreq_ondemand cpufreq_stats cpufreq_conservative freq_table cpufreq_userspace sbs sbshc container video output pci_slot battery ipv6 iptable_filter ip_tables x_tables ac sbp2 parport_pc lp parport snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore nvidia(P) pcspkr evdev snd_page_alloc i2c_core wmi shpchp button pci_hotplug ext3 jbd mbcache sr_mod cdrom usb_storage usbhid hid libusual ata_piix pata_acpi sd_mod crc_t10dif sg ata_generic ohci1394 ehci_hcd libata e1000 ieee1394 aacraid dock uhci_hcd scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
Feb 20 07:14:25 ROCK kernel: [29304.565001] CPU 4:
Feb 20 07:14:25 ROCK kernel: [29304.565001] Modules linked in: binfmt_misc rfcomm sco bridge stp bnep l2cap bluetooth ppdev acpi_cpufreq cpufreq_powersave cpufreq_ondemand cpufreq_stats cpufreq_conservative freq_table cpufreq_userspace sbs sbshc container video output pci_slot battery ipv6 iptable_filter ip_tables x_tables ac sbp2 parport_pc lp parport snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore nvidia(P) pcspkr evdev snd_page_alloc i2c_core wmi shpchp button pci_hotplug ext3 jbd mbcache sr_mod cdrom usb_storage usbhid hid libusual ata_piix pata_acpi sd_mod crc_t10dif sg ata_generic ohci1394 ehci_hcd libata e1000 ieee1394 aacraid dock uhci_hcd scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
Feb 20 07:14:25 ROCK kernel: [29304.565001] Pid: 20553, comm: pdflush Tainted: P      D   2.6.27-11-generic #1
Feb 20 07:14:25 ROCK kernel: [29304.565001] RIP: 0010:[<ffffffff8022d546>]  [<ffffffff8022d546>] __ticket_spin_lock+0x16/0x20
Feb 20 07:14:25 ROCK kernel: [29304.565001] RSP: 0018:ffff88020a7c3a10  EFLAGS: 00000293
Feb 20 07:14:25 ROCK kernel: [29304.565001] RAX: 0000000000009a98 RBX: ffff88020a7c3a10 RCX: 0000000000000000
Feb 20 07:14:25 ROCK kernel: [29304.565001] RDX: 0000000000000000 RSI: 0000000000000050 RDI: ffff880357002554
Feb 20 07:14:25 ROCK kernel: [29304.565001] RBP: ffffffff00000010 R08: 0000000000000000 R09: ffffffffa020aa30
Feb 20 07:14:25 ROCK kernel: [29304.565001] R10: 0000000000000001 R11: 0000000000000043 R12: ffff8803179f0460
Feb 20 07:14:25 ROCK kernel: [29304.565001] R13: ffffffff0000000c R14: ffff88028c4e38e0 R15: ffffffff00000010
Feb 20 07:14:25 ROCK kernel: [29304.565001] FS:  0000000000000000(0000) GS:ffff88035e46f400(0000) knlGS:0000000000000000
Feb 20 07:14:25 ROCK kernel: [29304.565001] CS:  0010 DS: 0018 ES: 0018 CR0: 000000008005003b
Feb 20 07:14:25 ROCK kernel: [29304.565001] CR2: 0000000001bbb478 CR3: 0000000000201000 CR4: 00000000000006e0
Feb 20 07:14:25 ROCK kernel: [29304.565001] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Feb 20 07:14:25 ROCK kernel: [29304.565001] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Feb 20 07:14:25 ROCK kernel: [29304.565001]
Feb 20 07:14:25 ROCK kernel: [29304.565001] Call Trace:
Feb 20 07:14:25 ROCK kernel: [29304.565001]  [<ffffffff8050367e>] ? _spin_lock+0xe/0x20
Feb 20 07:14:25 ROCK kernel: [29304.565001]  [<ffffffffa01f49cc>] ? journal_dirty_data+0x9c/0x240 [jbd]
Feb 20 07:14:25 ROCK kernel: [29304.565001]  [<ffffffffa0209b74>] ? ext3_journal_dirty_data+0x24/0x60 [ext3]
Feb 20 07:14:25 ROCK kernel: [29304.565001]  [<ffffffffa020aa4d>] ? journal_dirty_data_fn+0x1d/0x30 [ext3]
Feb 20 07:14:25 ROCK kernel: [29304.565001]  [<ffffffffa020a432>] ? walk_page_buffers+0x52/0xc0 [ext3]
Feb 20 07:14:25 ROCK kernel: [29304.565001]  [<ffffffffa020aa30>] ? journal_dirty_data_fn+0x0/0x30 [ext3]
Feb 20 07:14:25 ROCK kernel: [29304.565001]  [<ffffffffa020a7d4>] ? ext3_ordered_writepage+0x134/0x1b0 [ext3]
Feb 20 07:14:25 ROCK kernel: [29304.565001]  [<ffffffff802bbf2a>] ? __dec_zone_page_state+0x2a/0x30
Feb 20 07:14:25 ROCK kernel: [29304.565001]  [<ffffffff802b4487>] ? __writepage+0x17/0x50
Feb 20 07:14:25 ROCK kernel: [29304.565001]  [<ffffffff802b570d>] ? write_cache_pages+0x2bd/0x420
Feb 20 07:14:25 ROCK kernel: [29304.565001]  [<ffffffff802b4470>] ? __writepage+0x0/0x50
Feb 20 07:14:25 ROCK kernel: [29304.565001]  [<ffffffff802b5894>] ? generic_writepages+0x24/0x30
Feb 20 07:14:25 ROCK kernel: [29304.565001]  [<ffffffff802b58e5>] ? do_writepages+0x45/0x50
Feb 20 07:14:25 ROCK kernel: [29304.565001]  [<ffffffff8030ee1b>] ? __sync_single_inode+0x6b/0x2f0
Feb 20 07:14:25 ROCK kernel: [29304.565001]  [<ffffffff8030f0f8>] ? __writeback_single_inode+0x58/0x1b0
Feb 20 07:14:25 ROCK kernel: [29304.565001]  [<ffffffff8030f6b4>] ? generic_sync_sb_inodes+0x314/0x490
Feb 20 07:14:25 ROCK kernel: [29304.565001]  [<ffffffff8030fae2>] ? writeback_inodes+0x62/0x100
Feb 20 07:14:25 ROCK kernel: [29304.565001]  [<ffffffff802b48ac>] ? wb_kupdate+0xac/0x130
Feb 20 07:14:25 ROCK kernel: [29304.565001]  [<ffffffff802b60fe>] ? __pdflush+0x13e/0x220
Feb 20 07:14:25 ROCK kernel: [29304.565001]  [<ffffffff802b623b>] ? pdflush+0x5b/0x70
Feb 20 07:14:25 ROCK kernel: [29304.565001]  [<ffffffff802b4800>] ? wb_kupdate+0x0/0x130
Feb 20 07:14:25 ROCK kernel: [29304.565001]  [<ffffffff802b61e0>] ? pdflush+0x0/0x70
Feb 20 07:14:25 ROCK kernel: [29304.565001]  [<ffffffff80266c2e>] ? kthread+0x4e/0x90
Feb 20 07:14:25 ROCK kernel: [29304.565001]  [<ffffffff80213c99>] ? child_rip+0xa/0x11
Feb 20 07:14:25 ROCK kernel: [29304.565001]  [<ffffffff80266be0>] ? kthread+0x0/0x90
Feb 20 07:14:25 ROCK kernel: [29304.565001]  [<ffffffff80213c8f>] ? child_rip+0x0/0x11
Feb 20 07:14:25 ROCK kernel: [29304.565001]
Feb 20 07:14:29 ROCK kernel: [29307.784244] BUG: soft lockup - CPU#1 stuck for 61s! [kswapd0:281]
Feb 20 07:14:29 ROCK kernel: [29307.784248] Modules linked in: binfmt_misc rfcomm sco bridge stp bnep l2cap bluetooth ppdev acpi_cpufreq cpufreq_powersave cpufreq_ondemand cpufreq_stats cpufreq_conservative freq_table cpufreq_userspace sbs sbshc container video output pci_slot battery ipv6 iptable_filter ip_tables x_tables ac sbp2 parport_pc lp parport snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore nvidia(P) pcspkr evdev snd_page_alloc i2c_core wmi shpchp button pci_hotplug ext3 jbd mbcache sr_mod cdrom usb_storage usbhid hid libusual ata_piix pata_acpi sd_mod crc_t10dif sg ata_generic ohci1394 ehci_hcd libata e1000 ieee1394 aacraid dock uhci_hcd scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
Feb 20 07:14:29 ROCK kernel: [29307.784252] CPU 1:
Feb 20 07:14:29 ROCK kernel: [29307.784252] Modules linked in: binfmt_misc rfcomm sco bridge stp bnep l2cap bluetooth ppdev acpi_cpufreq cpufreq_powersave cpufreq_ondemand cpufreq_stats cpufreq_conservative freq_table cpufreq_userspace sbs sbshc container video output pci_slot battery ipv6 iptable_filter ip_tables x_tables ac sbp2 parport_pc lp parport snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore nvidia(P) pcspkr evdev snd_page_alloc i2c_core wmi shpchp button pci_hotplug ext3 jbd mbcache sr_mod cdrom usb_storage usbhid hid libusual ata_piix pata_acpi sd_mod crc_t10dif sg ata_generic ohci1394 ehci_hcd libata e1000 ieee1394 aacraid dock uhci_hcd scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
Feb 20 07:14:29 ROCK kernel: [29307.784252] Pid: 281, comm: kswapd0 Tainted: P      D   2.6.27-11-generic #1
Feb 20 07:14:29 ROCK kernel: [29307.784252] RIP: 0010:[<ffffffff8022d53e>]  [<ffffffff8022d53e>] __ticket_spin_lock+0xe/0x20
Feb 20 07:14:29 ROCK kernel: [29307.784252] RSP: 0018:ffff880358a0ba70  EFLAGS: 00000293
Feb 20 07:14:29 ROCK kernel: [29307.784252] RAX: 0000000000009b98 RBX: ffff880358a0ba70 RCX: ffff88032b2253d8
Feb 20 07:14:29 ROCK kernel: [29307.784252] RDX: 0000000000000000 RSI: ffff8801ef0dfaf0 RDI: ffff880357002554
Feb 20 07:14:29 ROCK kernel: [29307.784252] RBP: ffff880220e153e0 R08: ffff88035fc02800 R09: 0000000000000000
Feb 20 07:14:29 ROCK kernel: [29307.784252] R10: 0000000000000000 R11: 00000000ffffffff R12: ffffe20001bd7800
Feb 20 07:14:29 ROCK kernel: [29307.784252] R13: ffff88006f5e0000 R14: ffff88035fc0a800 R15: ffffffff802de677
Feb 20 07:14:29 ROCK kernel: [29307.784252] FS:  0000000000000000(0000) GS:ffff88035fc02980(0000) knlGS:0000000000000000
Feb 20 07:14:29 ROCK kernel: [29307.784252] CS:  0010 DS: 0018 ES: 0018 CR0: 000000008005003b
Feb 20 07:14:29 ROCK kernel: [29307.784252] CR2: 00000000012120f8 CR3: 0000000000201000 CR4: 00000000000006e0
Feb 20 07:14:29 ROCK kernel: [29307.784252] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Feb 20 07:14:29 ROCK kernel: [29307.784252] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Feb 20 07:14:29 ROCK kernel: [29307.784252]
Feb 20 07:14:29 ROCK kernel: [29307.784252] Call Trace:
Feb 20 07:14:29 ROCK kernel: [29307.784252]  [<ffffffff8050367e>] ? _spin_lock+0xe/0x20
Feb 20 07:14:29 ROCK kernel: [29307.784252]  [<ffffffffa01f440f>] ? __journal_try_to_free_buffer+0x5f/0xe0 [jbd]
Feb 20 07:14:29 ROCK kernel: [29307.784252]  [<ffffffffa01f450b>] ? journal_try_to_free_buffers+0x7b/0x130 [jbd]
Feb 20 07:14:29 ROCK kernel: [29307.784252]  [<ffffffffa020aa08>] ? ext3_releasepage+0x58/0x80 [ext3]
Feb 20 07:14:29 ROCK kernel: [29307.784252]  [<ffffffff802ac882>] ? try_to_release_page+0x32/0x60
Feb 20 07:14:29 ROCK kernel: [29307.784252]  [<ffffffff802b9bc7>] ? shrink_page_list+0x417/0x530
Feb 20 07:14:29 ROCK kernel: [29307.784252]  [<ffffffff802b90c9>] ? __isolate_lru_page+0x79/0xb0
Feb 20 07:14:29 ROCK kernel: [29307.784252]  [<ffffffff802b918a>] ? isolate_lru_pages+0x8a/0x220
Feb 20 07:14:29 ROCK kernel: [29307.784252]  [<ffffffff802b9e82>] ? shrink_inactive_list+0x1a2/0x4b0
Feb 20 07:14:29 ROCK kernel: [29307.784252]  [<ffffffff802ba20b>] ? shrink_zone+0x7b/0x160
Feb 20 07:14:29 ROCK kernel: [29307.784252]  [<ffffffff802baf83>] ? balance_pgdat+0x493/0x4c0
Feb 20 07:14:29 ROCK kernel: [29307.784252]  [<ffffffff802b9320>] ? isolate_pages_global+0x0/0x50
Feb 20 07:14:29 ROCK kernel: [29307.784252]  [<ffffffff802bb0ae>] ? kswapd+0xfe/0x150
Feb 20 07:14:29 ROCK kernel: [29307.784252]  [<ffffffff80267060>] ? autoremove_wake_function+0x0/0x40
Feb 20 07:14:29 ROCK kernel: [29307.784252]  [<ffffffff802bafb0>] ? kswapd+0x0/0x150
Feb 20 07:14:29 ROCK kernel: [29307.784252]  [<ffffffff80266c2e>] ? kthread+0x4e/0x90
Feb 20 07:14:29 ROCK kernel: [29307.784252]  [<ffffffff80213c99>] ? child_rip+0xa/0x11
Feb 20 07:14:29 ROCK kernel: [29307.784252]  [<ffffffff80266be0>] ? kthread+0x0/0x90
Feb 20 07:14:29 ROCK kernel: [29307.784252]  [<ffffffff80213c8f>] ? child_rip+0x0/0x11
Feb 20 07:14:29 ROCK kernel: [29307.784252]
Feb 20 07:15:17 ROCK kernel: [29356.101744] BUG: soft lockup - CPU#7 stuck for 61s! [nautilus:20306]
Feb 20 07:15:17 ROCK kernel: [29356.101748] Modules linked in: binfmt_misc rfcomm sco bridge stp bnep l2cap bluetooth ppdev acpi_cpufreq cpufreq_powersave cpufreq_ondemand cpufreq_stats cpufreq_conservative freq_table cpufreq_userspace sbs sbshc container video output pci_slot battery ipv6 iptable_filter ip_tables x_tables ac sbp2 parport_pc lp parport snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore nvidia(P) pcspkr evdev snd_page_alloc i2c_core wmi shpchp button pci_hotplug ext3 jbd mbcache sr_mod cdrom usb_storage usbhid hid libusual ata_piix pata_acpi sd_mod crc_t10dif sg ata_generic ohci1394 ehci_hcd libata e1000 ieee1394 aacraid dock uhci_hcd scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
Feb 20 07:15:17 ROCK kernel: [29356.101752] CPU 7:
Feb 20 07:15:17 ROCK kernel: [29356.101752] Modules linked in: binfmt_misc rfcomm sco bridge stp bnep l2cap bluetooth ppdev acpi_cpufreq cpufreq_powersave cpufreq_ondemand cpufreq_stats cpufreq_conservative freq_table cpufreq_userspace sbs sbshc container video output pci_slot battery ipv6 iptable_filter ip_tables x_tables ac sbp2 parport_pc lp parport snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore nvidia(P) pcspkr evdev snd_page_alloc i2c_core wmi shpchp button pci_hotplug ext3 jbd mbcache sr_mod cdrom usb_storage usbhid hid libusual ata_piix pata_acpi sd_mod crc_t10dif sg ata_generic ohci1394 ehci_hcd libata e1000 ieee1394 aacraid dock uhci_hcd scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
Feb 20 07:15:17 ROCK kernel: [29356.101752] Pid: 20306, comm: nautilus Tainted: P      D   2.6.27-11-generic #1
Feb 20 07:15:17 ROCK kernel: [29356.101752] RIP: 0010:[<ffffffff8022d546>]  [<ffffffff8022d546>] __ticket_spin_lock+0x16/0x20
Feb 20 07:15:17 ROCK kernel: [29356.101752] RSP: 0018:ffff88022a80ba58  EFLAGS: 00000297
Feb 20 07:15:17 ROCK kernel: [29356.101752] RAX: 0000000000009998 RBX: ffff88022a80ba58 RCX: 0000000000000000
Feb 20 07:15:17 ROCK kernel: [29356.101752] RDX: 0000000000000000 RSI: ffff880050f84d20 RDI: ffff880357002554
Feb 20 07:15:17 ROCK kernel: [29356.101752] RBP: ffff88022a80b9e8 R08: 0000000000000000 R09: ffffffffa0209b50
Feb 20 07:15:17 ROCK kernel: [29356.101752] R10: 0000000000000037 R11: 0000000000000000 R12: 0000000000000007
Feb 20 07:15:17 ROCK kernel: [29356.101752] R13: 0000000000000001 R14: 0000000000000001 R15: ffff8800280b14a0
Feb 20 07:15:17 ROCK kernel: [29356.101752] FS:  0000000040c6b950(0063) GS:ffff88035e46fe80(0000) knlGS:0000000000000000
Feb 20 07:15:17 ROCK kernel: [29356.101752] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Feb 20 07:15:17 ROCK kernel: [29356.101752] CR2: 00007f0ccaf92000 CR3: 0000000359ce3000 CR4: 00000000000006e0
Feb 20 07:15:17 ROCK kernel: [29356.101752] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Feb 20 07:15:17 ROCK kernel: [29356.101752] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Feb 20 07:15:17 ROCK kernel: [29356.101752]
Feb 20 07:15:17 ROCK kernel: [29356.101752] Call Trace:
Feb 20 07:15:17 ROCK kernel: [29356.101752]  [<ffffffff8050367e>] ? _spin_lock+0xe/0x20
Feb 20 07:15:17 ROCK kernel: [29356.101752]  [<ffffffffa01f49cc>] ? journal_dirty_data+0x9c/0x240 [jbd]
Feb 20 07:15:17 ROCK kernel: [29356.101752]  [<ffffffffa0209b74>] ? ext3_journal_dirty_data+0x24/0x60 [ext3]
Feb 20 07:15:17 ROCK kernel: [29356.101752]  [<ffffffffa020a432>] ? walk_page_buffers+0x52/0xc0 [ext3]
Feb 20 07:15:17 ROCK kernel: [29356.101752]  [<ffffffffa0209b50>] ? ext3_journal_dirty_data+0x0/0x60 [ext3]
Feb 20 07:15:17 ROCK kernel: [29356.101752]  [<ffffffffa020a8c7>] ? ext3_ordered_write_end+0x77/0x160 [ext3]
Feb 20 07:15:17 ROCK kernel: [29356.101752]  [<ffffffff802ab92f>] ? generic_perform_write+0x11f/0x1c0
Feb 20 07:15:17 ROCK kernel: [29356.101752]  [<ffffffffa021c24b>] ? ext3_xattr_security_get+0x2b/0x30 [ext3]
Feb 20 07:15:17 ROCK kernel: [29356.101752]  [<ffffffffa021c24b>] ? ext3_xattr_security_get+0x2b/0x30 [ext3]
Feb 20 07:15:17 ROCK kernel: [29356.101752]  [<ffffffff802ad632>] ? generic_file_buffered_write+0x92/0x170
Feb 20 07:15:17 ROCK kernel: [29356.101752]  [<ffffffff802ae951>] ? __generic_file_aio_write_nolock+0x261/0x470
Feb 20 07:15:17 ROCK kernel: [29356.101752]  [<ffffffff802aec6c>] ? generic_file_aio_write+0x6c/0xd0
Feb 20 07:15:17 ROCK kernel: [29356.101752]  [<ffffffffa0207ccb>] ? ext3_file_write+0x2b/0xd0 [ext3]
Feb 20 07:15:17 ROCK kernel: [29356.101752]  [<ffffffff802e9b19>] ? do_sync_write+0xf9/0x140
Feb 20 07:15:17 ROCK kernel: [29356.101752]  [<ffffffff80267060>] ? autoremove_wake_function+0x0/0x40
Feb 20 07:15:17 ROCK kernel: [29356.101752]  [<ffffffff803873a1>] ? aa_file_permission+0x21/0xf0
Feb 20 07:15:17 ROCK kernel: [29356.101752]  [<ffffffff803874c8>] ? apparmor_file_permission+0x28/0x30
Feb 20 07:15:17 ROCK kernel: [29356.101752]  [<ffffffff80361f76>] ? security_file_permission+0x16/0x20
Feb 20 07:15:17 ROCK kernel: [29356.101752]  [<ffffffff802ea1db>] ? vfs_write+0xcb/0x130
Feb 20 07:15:17 ROCK kernel: [29356.101752]  [<ffffffff802ea335>] ? sys_write+0x55/0x90
Feb 20 07:15:17 ROCK kernel: [29356.101752]  [<ffffffff8021285a>] ? system_call_fastpath+0x16/0x1b
Feb 20 07:15:17 ROCK kernel: [29356.101752]
Feb 20 07:15:31 ROCK kernel: [29370.060993] BUG: soft lockup - CPU#4 stuck for 61s! [pdflush:20553]
Feb 20 07:15:31 ROCK kernel: [29370.060998] Modules linked in: binfmt_misc rfcomm sco bridge stp bnep l2cap bluetooth ppdev acpi_cpufreq cpufreq_powersave cpufreq_ondemand cpufreq_stats cpufreq_conservative freq_table cpufreq_userspace sbs sbshc container video output pci_slot battery ipv6 iptable_filter ip_tables x_tables ac sbp2 parport_pc lp parport snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore nvidia(P) pcspkr evdev snd_page_alloc i2c_core wmi shpchp button pci_hotplug ext3 jbd mbcache sr_mod cdrom usb_storage usbhid hid libusual ata_piix pata_acpi sd_mod crc_t10dif sg ata_generic ohci1394 ehci_hcd libata e1000 ieee1394 aacraid dock uhci_hcd scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
Feb 20 07:15:31 ROCK kernel: [29370.061002] CPU 4:
Feb 20 07:15:31 ROCK kernel: [29370.061002] Modules linked in: binfmt_misc rfcomm sco bridge stp bnep l2cap bluetooth ppdev acpi_cpufreq cpufreq_powersave cpufreq_ondemand cpufreq_stats cpufreq_conservative freq_table cpufreq_userspace sbs sbshc container video output pci_slot battery ipv6 iptable_filter ip_tables x_tables ac sbp2 parport_pc lp parport snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore nvidia(P) pcspkr evdev snd_page_alloc i2c_core wmi shpchp button pci_hotplug ext3 jbd mbcache sr_mod cdrom usb_storage usbhid hid libusual ata_piix pata_acpi sd_mod crc_t10dif sg ata_generic ohci1394 ehci_hcd libata e1000 ieee1394 aacraid dock uhci_hcd scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
Feb 20 07:15:31 ROCK kernel: [29370.061002] Pid: 20553, comm: pdflush Tainted: P      D   2.6.27-11-generic #1
Feb 20 07:15:31 ROCK kernel: [29370.061002] RIP: 0010:[<ffffffff8022d544>]  [<ffffffff8022d544>] __ticket_spin_lock+0x14/0x20
Feb 20 07:15:31 ROCK kernel: [29370.061002] RSP: 0018:ffff88020a7c3a10  EFLAGS: 00000293
Feb 20 07:15:31 ROCK kernel: [29370.061002] RAX: 0000000000009a98 RBX: ffff88020a7c3a10 RCX: 0000000000000000
Feb 20 07:15:31 ROCK kernel: [29370.061002] RDX: 0000000000000000 RSI: 0000000000000050 RDI: ffff880357002554
Feb 20 07:15:31 ROCK kernel: [29370.061002] RBP: ffffffff00000010 R08: 0000000000000000 R09: ffffffffa020aa30
Feb 20 07:15:31 ROCK kernel: [29370.061002] R10: 0000000000000001 R11: 0000000000000043 R12: ffff8803179f0460
Feb 20 07:15:31 ROCK kernel: [29370.061002] R13: ffffffff0000000c R14: ffff88028c4e38e0 R15: ffffffff00000010
Feb 20 07:15:31 ROCK kernel: [29370.061002] FS:  0000000000000000(0000) GS:ffff88035e46f400(0000) knlGS:0000000000000000
Feb 20 07:15:31 ROCK kernel: [29370.061002] CS:  0010 DS: 0018 ES: 0018 CR0: 000000008005003b
Feb 20 07:15:31 ROCK kernel: [29370.061002] CR2: 0000000001bbb478 CR3: 0000000000201000 CR4: 00000000000006e0
Feb 20 07:15:31 ROCK kernel: [29370.061002] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Feb 20 07:15:31 ROCK kernel: [29370.061002] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Feb 20 07:15:31 ROCK kernel: [29370.061002]
Feb 20 07:15:31 ROCK kernel: [29370.061002] Call Trace:
Feb 20 07:15:31 ROCK kernel: [29370.061002]  [<ffffffff8050367e>] ? _spin_lock+0xe/0x20
Feb 20 07:15:31 ROCK kernel: [29370.061002]  [<ffffffffa01f49cc>] ? journal_dirty_data+0x9c/0x240 [jbd]
Feb 20 07:15:31 ROCK kernel: [29370.061002]  [<ffffffffa0209b74>] ? ext3_journal_dirty_data+0x24/0x60 [ext3]
Feb 20 07:15:31 ROCK kernel: [29370.061002]  [<ffffffffa020aa4d>] ? journal_dirty_data_fn+0x1d/0x30 [ext3]
Feb 20 07:15:31 ROCK kernel: [29370.061002]  [<ffffffffa020a432>] ? walk_page_buffers+0x52/0xc0 [ext3]
Feb 20 07:15:31 ROCK kernel: [29370.061002]  [<ffffffffa020aa30>] ? journal_dirty_data_fn+0x0/0x30 [ext3]
Feb 20 07:15:31 ROCK kernel: [29370.061002]  [<ffffffffa020a7d4>] ? ext3_ordered_writepage+0x134/0x1b0 [ext3]
Feb 20 07:15:31 ROCK kernel: [29370.061002]  [<ffffffff802bbf2a>] ? __dec_zone_page_state+0x2a/0x30
Feb 20 07:15:31 ROCK kernel: [29370.061002]  [<ffffffff802b4487>] ? __writepage+0x17/0x50
Feb 20 07:15:31 ROCK kernel: [29370.061002]  [<ffffffff802b570d>] ? write_cache_pages+0x2bd/0x420
Feb 20 07:15:31 ROCK kernel: [29370.061002]  [<ffffffff802b4470>] ? __writepage+0x0/0x50
Feb 20 07:15:31 ROCK kernel: [29370.061002]  [<ffffffff802b5894>] ? generic_writepages+0x24/0x30
Feb 20 07:15:31 ROCK kernel: [29370.061002]  [<ffffffff802b58e5>] ? do_writepages+0x45/0x50
Feb 20 07:15:31 ROCK kernel: [29370.061002]  [<ffffffff8030ee1b>] ? __sync_single_inode+0x6b/0x2f0
Feb 20 07:15:31 ROCK kernel: [29370.061002]  [<ffffffff8030f0f8>] ? __writeback_single_inode+0x58/0x1b0
Feb 20 07:15:31 ROCK kernel: [29370.061002]  [<ffffffff8030f6b4>] ? generic_sync_sb_inodes+0x314/0x490
Feb 20 07:15:31 ROCK kernel: [29370.061002]  [<ffffffff8030fae2>] ? writeback_inodes+0x62/0x100
Feb 20 07:15:31 ROCK kernel: [29370.061002]  [<ffffffff802b48ac>] ? wb_kupdate+0xac/0x130
Feb 20 07:15:31 ROCK kernel: [29370.061002]  [<ffffffff802b60fe>] ? __pdflush+0x13e/0x220
Feb 20 07:15:31 ROCK kernel: [29370.061002]  [<ffffffff802b623b>] ? pdflush+0x5b/0x70
Feb 20 07:15:31 ROCK kernel: [29370.061002]  [<ffffffff802b4800>] ? wb_kupdate+0x0/0x130
Feb 20 07:15:31 ROCK kernel: [29370.061002]  [<ffffffff802b61e0>] ? pdflush+0x0/0x70
Feb 20 07:15:31 ROCK kernel: [29370.061002]  [<ffffffff80266c2e>] ? kthread+0x4e/0x90
Feb 20 07:15:31 ROCK kernel: [29370.061002]  [<ffffffff80213c99>] ? child_rip+0xa/0x11
Feb 20 07:15:31 ROCK kernel: [29370.061002]  [<ffffffff80266be0>] ? kthread+0x0/0x90
Feb 20 07:15:31 ROCK kernel: [29370.061002]  [<ffffffff80213c8f>] ? child_rip+0x0/0x11

---

### Post by Kevbert on 2009-02-21
Can you run memtest from the boot menu for a couple of passes ?

---

### Post by kinsei on 2009-02-21
Thanks for the memory check suggestion.  

It failed the first time, and I proceeded to try and determine which DIMM it was.  After successfully testing all of the DIMMS in slot 1, I confirmed the issue was one with a specific motherboard DIMM slot, which started actually causing a reboot each time I plugged any of the DIMMs into it. 

I have started the RMA process and hopefully this fixes my issue.  I'll let you know how it goes.

---

