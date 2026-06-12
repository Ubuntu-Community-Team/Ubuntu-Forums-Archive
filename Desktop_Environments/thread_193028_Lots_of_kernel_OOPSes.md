---
title: "Lots of kernel OOPSes"
date: 2006-06-09
forum: Desktop Environments
---

### Post by sswords on 2006-06-09
I'm wondering if anyone knows what's likely to be the cause of all the crashes I've had lately.

I've just updated to Dapper and I'm getting a lot of system freezes which seem to be associated with OOPS messages in /var/log/kern.log.  I've tried shutting ACPI off, which people seem to recommend often for this sort of thing, but it doesn't seem to get rid of them.  I've just switched to the nv driver (instead of nvidia legacy, since I have an old Geforce2 GTS) and I'm hoping that helps, but I don't have any real reason yet to believe it will.  For some reason the problems seem to occur whenever I run Azureus; I'm not sure if it's unique to that program or if it's a java thing, but since my system as a whole seems pretty unstable I don't want to blame just one program.  I had a similar problem with Breezy which I solved by using a custom kernel, but I'd rather not resort to that again yet.

Possibly relevant notes about my system:
Athlon Thunderbird 1.2 GHz, 512MB RAM
Nvidia Geforce2 GTS
Running official Ubuntu Dapper kernel 2.6.15-23-k7

If anyone knows how to decode these, here are some of the log messages:
```

Jun  9 11:28:47 localhost kernel: [43987.936027] Unable to handle kernel paging request at virtual address 80778bd2
Jun  9 11:28:47 localhost kernel: [43987.936075]  printing eip:
Jun  9 11:28:47 localhost kernel: [43987.936078] c0173535
Jun  9 11:28:47 localhost kernel: [43987.936081] *pde = 00000000
Jun  9 11:28:47 localhost kernel: [43987.936086] Oops: 0000 [#1]
Jun  9 11:28:47 localhost kernel: [43987.936089] PREEMPT SMP 
Jun  9 11:28:47 localhost kernel: [43987.936093] Modules linked in: nls_utf8 udf binfmt_misc ipv6 apm nls_iso8859_1 nls_cp437 vfat fat ext3 jbd dm_mod md_mod af_packet sr_mod sbp2 scsi_mod lp rsrc_nonstatic pcmcia_core snd_emu10k1_synth snd_emux_synth snd_seq_virmidi snd_seq_midi_emul snd_seq_dummy snd_seq_oss snd_seq_midi snd_seq_midi_event snd_seq snd_emu10k1 snd_rawmidi snd_ac97_codec snd_ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_device snd_timer snd_page_alloc snd_util_mem nvidia snd_hwdep i2c_viapro via686a i2c_isa via_agp snd tsdev 8139too 8139cp i2c_core agpgart soundcore mii shpchp pci_hotplug pcspkr floppy emu10k1_gp gameport psmouse serio_raw parport_pc parport evdev reiserfs ide_generic ehci_hcd ohci1394 ieee1394 uhci_hcd ohci_hcd usbcore hpt366 ide_disk ide_cd cdrom generic via82cxxx processor capability commoncap vga16fb vgastate fbcon tileblit font bitblit softcursor
Jun  9 11:28:47 localhost kernel: [43987.936159] CPU:    0
Jun  9 11:28:47 localhost kernel: [43987.936161] EIP:    0060:[__block_write_full_page+213/896]    Tainted: P S    VLI
Jun  9 11:28:47 localhost kernel: [43987.936164] EFLAGS: 00210297   (2.6.15-23-k7) 
Jun  9 11:28:47 localhost kernel: [43987.936183] EIP is at __block_write_full_page+0xd5/0x380
Jun  9 11:28:47 localhost kernel: [43987.936188] eax: 10fa9c2a   ebx: 80778bd2   ecx: 00000003   edx: 00000009
Jun  9 11:28:47 localhost kernel: [43987.936193] esi: 000141a1   edi: 00000000   ebp: d8536c9c   esp: de9add60
Jun  9 11:28:47 localhost kernel: [43987.936198] ds: 007b   es: 007b   ss: 0068
Jun  9 11:28:47 localhost kernel: [43987.936203] Process pdflush (pid: 73, threadinfo=de9ac000 task=dffd0030)
Jun  9 11:28:47 localhost kernel: [43987.936206] Stack: 00000001 d5cacda0 de9add70 00000000 00002835 00000000 00033e47 00000000 
Jun  9 11:28:47 localhost kernel: [43987.936216]        067c9000 00000000 00000001 dbd11e5c c0175058 dbd11e5c c107d5bc e0f73b20 
Jun  9 11:28:47 localhost kernel: [43987.936226]        de9adf34 00000000 c107d5bc 0000000d 00000001 de9adf34 e0f73cef c107d5bc 
Jun  9 11:28:47 localhost kernel: [43987.936235] Call Trace:
Jun  9 11:28:47 localhost kernel: [43987.936273]  [block_write_full_page+280/288] block_write_full_page+0x118/0x120
Jun  9 11:28:47 localhost kernel: [43987.936284]  [pg0+548518688/1069179904] fat_get_block+0x0/0x1b0 [fat]
Jun  9 11:28:47 localhost kernel: [43987.936326]  [pg0+548519151/1069179904] fat_writepage+0x1f/0x30 [fat]
Jun  9 11:28:47 localhost kernel: [43987.936342]  [pg0+548518688/1069179904] fat_get_block+0x0/0x1b0 [fat]
Jun  9 11:28:47 localhost kernel: [43987.936357]  [mpage_writepages+605/1088] mpage_writepages+0x25d/0x440
Jun  9 11:28:47 localhost kernel: [43987.936377]  [__find_get_block+207/288] __find_get_block+0xcf/0x120
Jun  9 11:28:47 localhost kernel: [43987.936390]  [pg0+548519120/1069179904] fat_writepage+0x0/0x30 [fat]
Jun  9 11:28:47 localhost kernel: [43987.936441]  [do_writepages+57/64] do_writepages+0x39/0x40
Jun  9 11:28:47 localhost kernel: [43987.936457]  [__sync_single_inode+111/608] __sync_single_inode+0x6f/0x260
Jun  9 11:28:47 localhost kernel: [43987.936475]  [__writeback_single_inode+74/416] __writeback_single_inode+0x4a/0x1a0
Jun  9 11:28:47 localhost kernel: [43987.936489]  [pg0+542821804/1069179904] journal_end_sync+0x7c/0x90 [reiserfs]
Jun  9 11:28:47 localhost kernel: [43987.936578]  [sync_sb_inodes+494/752] sync_sb_inodes+0x1ee/0x2f0
Jun  9 11:28:47 localhost kernel: [43987.936598]  [writeback_inodes+114/256] writeback_inodes+0x72/0x100
Jun  9 11:28:47 localhost kernel: [43987.936610]  [background_writeout+152/224] background_writeout+0x98/0xe0
Jun  9 11:28:47 localhost kernel: [43987.936650]  [pdflush+0/80] pdflush+0x0/0x50
Jun  9 11:28:47 localhost kernel: [43987.936656]  [__pdflush+226/416] __pdflush+0xe2/0x1a0
Jun  9 11:28:47 localhost kernel: [43987.936667]  [pdflush+60/80] pdflush+0x3c/0x50
Jun  9 11:28:47 localhost kernel: [43987.936676]  [background_writeout+0/224] background_writeout+0x0/0xe0
Jun  9 11:28:47 localhost kernel: [43987.936690]  [kthread+199/208] kthread+0xc7/0xd0
Jun  9 11:28:47 localhost kernel: [43987.936704]  [kthread+0/208] kthread+0x0/0xd0
Jun  9 11:28:47 localhost kernel: [43987.936714]  [kernel_thread_helper+5/12] kernel_thread_helper+0x5/0xc
Jun  9 11:28:47 localhost kernel: [43987.936727] Code: 89 eb eb 21 89 f6 77 06 3b 74 24 18 76 1d 90 0f ba 33 01 90 0f ba 2b 00 8b 5b 04 83 c6 01 83 d7 00 39 dd 74 71 3b 7c 24 1c 73 db <8b> 03 a8 20 75 e7 8b 03 a8 02 74 e1 8b 54 24 34 c7 44 24 10 01 
Jun  9 11:28:47 localhost kernel: [43987.936765]  <1>Unable to handle kernel paging request at virtual address 4ea8967f
Jun  9 11:28:47 localhost kernel: [43988.023180]  printing eip:
Jun  9 11:28:47 localhost kernel: [43988.023184] c0173535
Jun  9 11:28:47 localhost kernel: [43988.023187] *pde = 00000000
Jun  9 11:28:47 localhost kernel: [43988.023192] Oops: 0000 [#2]
Jun  9 11:28:47 localhost kernel: [43988.023195] PREEMPT SMP 
Jun  9 11:28:47 localhost kernel: [43988.023199] Modules linked in: nls_utf8 udf binfmt_misc ipv6 apm nls_iso8859_1 nls_cp437 vfat fat ext3 jbd dm_mod md_mod af_packet sr_mod sbp2 scsi_mod lp rsrc_nonstatic pcmcia_core snd_emu10k1_synth snd_emux_synth snd_seq_virmidi snd_seq_midi_emul snd_seq_dummy snd_seq_oss snd_seq_midi snd_seq_midi_event snd_seq snd_emu10k1 snd_rawmidi snd_ac97_codec snd_ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_device snd_timer snd_page_alloc snd_util_mem nvidia snd_hwdep i2c_viapro via686a i2c_isa via_agp snd tsdev 8139too 8139cp i2c_core agpgart soundcore mii shpchp pci_hotplug pcspkr floppy emu10k1_gp gameport psmouse serio_raw parport_pc parport evdev reiserfs ide_generic ehci_hcd ohci1394 ieee1394 uhci_hcd ohci_hcd usbcore hpt366 ide_disk ide_cd cdrom generic via82cxxx processor capability commoncap vga16fb vgastate fbcon tileblit font bitblit softcursor
Jun  9 11:28:47 localhost kernel: [43988.023266] CPU:    0
Jun  9 11:28:47 localhost kernel: [43988.023268] EIP:    0060:[__block_write_full_page+213/896]    Tainted: P S    VLI
Jun  9 11:28:47 localhost kernel: [43988.023270] EFLAGS: 00210287   (2.6.15-23-k7) 
Jun  9 11:28:47 localhost kernel: [43988.023290] EIP is at __block_write_full_page+0xd5/0x380
Jun  9 11:28:47 localhost kernel: [43988.023295] eax: 00000000   ebx: 4ea8967f   ecx: 00000012   edx: 00000001
Jun  9 11:28:47 localhost kernel: [43988.023300] esi: 000141af   edi: 00000000   ebp: d1440cd0   esp: de9b1d80
Jun  9 11:28:47 localhost kernel: [43988.023305] ds: 007b   es: 007b   ss: 0068
Jun  9 11:28:47 localhost kernel: [43988.023310] Process kswapd0 (pid: 75, threadinfo=de9b0000 task=dff48580)
Jun  9 11:28:47 localhost kernel: [43988.023313] Stack: d9f6eaa0 024dc756 00000000 d8536d04 00000001 00000000 00036367 00000000 
Jun  9 11:28:47 localhost kernel: [43988.023323]        06c6d000 00000000 de9b1e20 dbd11e5c c0175058 dbd11e5c c10fbb80 e0f73b20 
Jun  9 11:28:47 localhost kernel: [43988.023333]        de9b1df8 00000000 c10fbb80 c030d1e8 de9b1e20 dbd11f14 e0f73cef c10fbb80 
Jun  9 11:28:47 localhost kernel: [43988.023343] Call Trace:
Jun  9 11:28:47 localhost kernel: [43988.023379]  [block_write_full_page+280/288] block_write_full_page+0x118/0x120
Jun  9 11:28:47 localhost kernel: [43988.023390]  [pg0+548518688/1069179904] fat_get_block+0x0/0x1b0 [fat]
Jun  9 11:28:47 localhost kernel: [43988.023432]  [pg0+548519151/1069179904] fat_writepage+0x1f/0x30 [fat]
Jun  9 11:28:47 localhost kernel: [43988.023447]  [pg0+548518688/1069179904] fat_get_block+0x0/0x1b0 [fat]
Jun  9 11:28:47 localhost kernel: [43988.023462]  [pageout+174/336] pageout+0xae/0x150
Jun  9 11:28:47 localhost kernel: [43988.023500]  [shrink_list+755/1120] shrink_list+0x2f3/0x460
Jun  9 11:28:47 localhost kernel: [43988.023535]  [__pagevec_release+37/48] __pagevec_release+0x25/0x30
Jun  9 11:28:47 localhost kernel: [43988.023553]  [shrink_cache+283/688] shrink_cache+0x11b/0x2b0
Jun  9 11:28:47 localhost kernel: [43988.023603]  [shrink_zone+150/240] shrink_zone+0x96/0xf0
Jun  9 11:28:47 localhost kernel: [43988.023619]  [balance_pgdat+503/1040] balance_pgdat+0x1f7/0x410
Jun  9 11:28:47 localhost kernel: [43988.023661]  [kswapd+230/320] kswapd+0xe6/0x140
Jun  9 11:28:47 localhost kernel: [43988.023674]  [autoremove_wake_function+0/96] autoremove_wake_function+0x0/0x60
Jun  9 11:28:47 localhost kernel: [43988.023687]  [kswapd+0/320] kswapd+0x0/0x140
Jun  9 11:28:47 localhost kernel: [43988.023697]  [kernel_thread_helper+5/12] kernel_thread_helper+0x5/0xc
Jun  9 11:28:47 localhost kernel: [43988.023711] Code: 89 eb eb 21 89 f6 77 06 3b 74 24 18 76 1d 90 0f ba 33 01 90 0f ba 2b 00 8b 5b 04 83 c6 01 83 d7 00 39 dd 74 71 3b 7c 24 1c 73 db <8b> 03 a8 20 75 e7 8b 03 a8 02 74 e1 8b 54 24 34 c7 44 24 10 01 
Jun  9 11:28:47 localhost kernel: [43988.023751]  <1>Unable to handle kernel paging request at virtual address 69c43f5d
Jun  9 11:28:47 localhost kernel: [43988.144097]  printing eip:
Jun  9 11:28:47 localhost kernel: [43988.144102] e09e7a50
Jun  9 11:28:47 localhost kernel: [43988.144105] *pde = 00000000
Jun  9 11:28:47 localhost kernel: [43988.144109] Oops: 0000 [#3]
Jun  9 11:28:47 localhost kernel: [43988.144111] PREEMPT SMP 
Jun  9 11:28:47 localhost kernel: [43988.144116] Modules linked in: nls_utf8 udf binfmt_misc ipv6 apm nls_iso8859_1 nls_cp437 vfat fat ext3 jbd dm_mod md_mod af_packet sr_mod sbp2 scsi_mod lp rsrc_nonstatic pcmcia_core snd_emu10k1_synth snd_emux_synth snd_seq_virmidi snd_seq_midi_emul snd_seq_dummy snd_seq_oss snd_seq_midi snd_seq_midi_event snd_seq snd_emu10k1 snd_rawmidi snd_ac97_codec snd_ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_device snd_timer snd_page_alloc snd_util_mem nvidia snd_hwdep i2c_viapro via686a i2c_isa via_agp snd tsdev 8139too 8139cp i2c_core agpgart soundcore mii shpchp pci_hotplug pcspkr floppy emu10k1_gp gameport psmouse serio_raw parport_pc parport evdev reiserfs ide_generic ehci_hcd ohci1394 ieee1394 uhci_hcd ohci_hcd usbcore hpt366 ide_disk ide_cd cdrom generic via82cxxx processor capability commoncap vga16fb vgastate fbcon tileblit font bitblit softcursor
Jun  9 11:28:47 localhost kernel: [43988.144184] CPU:    0
Jun  9 11:28:47 localhost kernel: [43988.144186] EIP:    0060:[pg0+542702160/1069179904]    Tainted: P S    VLI
Jun  9 11:28:47 localhost kernel: [43988.144188] EFLAGS: 00210a06   (2.6.15-23-k7) 
Jun  9 11:28:47 localhost kernel: [43988.144248] EIP is at reiserfs_releasepage+0x40/0xd0 [reiserfs]
Jun  9 11:28:47 localhost kernel: [43988.144254] eax: 00000000   ebx: 69c43f35   ecx: e09e7a10   edx: c137c440
Jun  9 11:28:47 localhost kernel: [43988.144260] esi: d8536d38   edi: c137c440   ebp: e0e7b0ec   esp: cd52fac4
Jun  9 11:28:47 localhost kernel: [43988.144264] ds: 007b   es: 007b   ss: 0068
Jun  9 11:28:47 localhost kernel: [43988.144269] Process java (pid: 10943, threadinfo=cd52e000 task=c8786560)
Jun  9 11:28:47 localhost kernel: [43988.144272] Stack: c6bc73dc cd52fbc0 cd52fc24 c014c8ee c6bc73dc c137c440 cd52fbc0 cd52fc24 
Jun  9 11:28:47 localhost kernel: [43988.144283]        c015a406 c137c440 000200d2 c6bc73ec 00000000 00000019 00000001 00000000 
Jun  9 11:28:47 localhost kernel: [43988.144293]        0000000b 00000001 c1103a10 c13a203c c1128628 c12c4300 c13fe388 c143d1fc 
Jun  9 11:28:47 localhost kernel: [43988.144302] Call Trace:
Jun  9 11:28:47 localhost kernel: [43988.144320]  [__remove_from_page_cache+30/96] __remove_from_page_cache+0x1e/0x60
Jun  9 11:28:47 localhost kernel: [43988.144342]  [shrink_list+998/1120] shrink_list+0x3e6/0x460
Jun  9 11:28:47 localhost kernel: [43988.144396]  [shrink_cache+283/688] shrink_cache+0x11b/0x2b0
Jun  9 11:28:47 localhost kernel: [43988.144447]  [shrink_zone+150/240] shrink_zone+0x96/0xf0
Jun  9 11:28:47 localhost kernel: [43988.144463]  [shrink_caches+100/128] shrink_caches+0x64/0x80
Jun  9 11:28:47 localhost kernel: [43988.144475]  [try_to_free_pages+166/464] try_to_free_pages+0xa6/0x1d0
Jun  9 11:28:47 localhost kernel: [43988.144508]  [__alloc_pages+354/816] __alloc_pages+0x162/0x330
Jun  9 11:28:47 localhost kernel: [43988.144538]  [find_or_create_page+152/208] find_or_create_page+0x98/0xd0
Jun  9 11:28:47 localhost kernel: [43988.144561]  [cont_prepare_write+81/656] cont_prepare_write+0x51/0x290
Jun  9 11:28:47 localhost kernel: [43988.144577]  [pg0+548518688/1069179904] fat_get_block+0x0/0x1b0 [fat]
Jun  9 11:28:47 localhost kernel: [43988.144618]  [pg0+548519251/1069179904] fat_prepare_write+0x33/0x40 [fat]
Jun  9 11:28:47 localhost kernel: [43988.144636]  [pg0+548518688/1069179904] fat_get_block+0x0/0x1b0 [fat]
Jun  9 11:28:47 localhost kernel: [43988.144651]  [generic_file_buffered_write+722/1808] generic_file_buffered_write+0x2d2/0x710
Jun  9 11:28:47 localhost kernel: [43988.144696]  [__mark_inode_dirty+109/464] __mark_inode_dirty+0x6d/0x1d0
Jun  9 11:28:47 localhost kernel: [43988.144710]  [inode_update_time+80/224] inode_update_time+0x50/0xe0
Jun  9 11:28:47 localhost kernel: [43988.144729]  [__generic_file_aio_write_nolock+696/1280] __generic_file_aio_write_nolock+0x2b8/0x500
Jun  9 11:28:47 localhost kernel: [43988.144775]  [__generic_file_write_nolock+166/208] __generic_file_write_nolock+0xa6/0xd0
Jun  9 11:28:47 localhost kernel: [43988.144800]  [buffered_rmqueue+296/608] buffered_rmqueue+0x128/0x260
Jun  9 11:28:47 localhost kernel: [43988.144825]  [autoremove_wake_function+0/96] autoremove_wake_function+0x0/0x60
Jun  9 11:28:47 localhost kernel: [43988.144841]  [find_get_page+70/96] find_get_page+0x46/0x60
Jun  9 11:28:47 localhost kernel: [43988.144849]  [generic_file_writev+74/224] generic_file_writev+0x4a/0xe0
Jun  9 11:28:47 localhost kernel: [43988.144872]  [do_readv_writev+667/816] do_readv_writev+0x29b/0x330
Jun  9 11:28:47 localhost kernel: [43988.144890]  [do_sync_write+0/304] do_sync_write+0x0/0x130
Jun  9 11:28:47 localhost kernel: [43988.144915]  [run_timer_softirq+303/464] run_timer_softirq+0x12f/0x1d0
Jun  9 11:28:47 localhost kernel: [43988.144931]  [timer_interrupt+98/176] timer_interrupt+0x62/0xb0
Jun  9 11:28:47 localhost kernel: [43988.144953]  [vfs_writev+76/112] vfs_writev+0x4c/0x70
Jun  9 11:28:47 localhost kernel: [43988.144966]  [sys_writev+75/176] sys_writev+0x4b/0xb0
Jun  9 11:28:47 localhost kernel: [43988.144984]  [sysenter_past_esp+84/117] sysenter_past_esp+0x54/0x75
Jun  9 11:28:47 localhost kernel: [43988.145014] Code: 00 8b 80 88 01 00 00 8b 58 0c 8b 07 f6 c4 01 75 74 8d ab ec 00 00 00 89 e8 e8 7d 2d 92 df 8b 07 f6 c4 08 74 56 8b 77 0c 89 f3 90 <8b> 43 28 85 c0 74 14 8b 03 a8 02 75 30 8b 03 a8 04 75 2a 89 1c 

Jun  9 11:35:51 localhost kernel: [4295023.549000] Unable to handle kernel paging request at virtual address 48a31a05
Jun  9 11:35:51 localhost kernel: [4295023.549000]  printing eip:
Jun  9 11:35:51 localhost kernel: [4295023.549000] c01f68a9
Jun  9 11:35:51 localhost kernel: [4295023.549000] *pde = 00000000
Jun  9 11:35:51 localhost kernel: [4295023.549000] Oops: 0000 [#1]
Jun  9 11:35:51 localhost kernel: [4295023.549000] PREEMPT SMP 
Jun  9 11:35:51 localhost kernel: [4295023.549000] Modules linked in: nls_utf8 udf binfmt_misc ipt_TCPMSS ipt_limit ip_nat_irc ip_nat_ftp iptable_nat iptable_mangle ipt_LOG ipt_MASQUERADE ip_nat ipt_TOS ipt_REJECT ip_conntrack_irc ip_conntrack_ftp ipt_state ip_conntrack nfnetlink iptable_filter ip_tables tc1100_wmi video acpi_sbs battery i2c_acpi_ec container button pcc_acpi sony_acpi ac dev_acpi hotkey nls_iso8859_1 nls_cp437 vfat fat ext3 jbd ipv6 dm_mod md_mod af_packet sr_mod sbp2 scsi_mod lp rsrc_nonstatic pcmcia_core tsdev floppy pcspkr psmouse serio_raw snd_emu10k1_synth snd_emux_synth snd_seq_virmidi snd_seq_midi_emul snd_seq_dummy snd_seq_oss snd_seq_midi snd_seq_midi_event snd_seq emu10k1_gp snd_emu10k1 snd_rawmidi snd_ac97_codec snd_ac97_bus gameport snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_device snd_timer snd_page_alloc snd_util_mem snd_hwdep snd soundcore i2c_viapro via686a i2c_isa nvidia i2c_core parport_pc parport via_agp shpchp pci_hotplug 8139too 8139cp agpgart mii evdev reiserfs ide_generic ohc
Jun  9 11:35:51 localhost kernel: 1394 ieee1394 ehci_hcd uhci_hcd ohci_hcd usbcore hpt366 ide_disk ide_cd cdrom generic via82cxxx thermal processor fan capability commoncap vga16fb vgastate fbcon tileblit font bitblit softcursor
Jun  9 11:35:51 localhost kernel: [4295023.549000] CPU:    0
Jun  9 11:35:51 localhost kernel: [4295023.549000] EIP:    0060:[radix_tree_lookup+121/144]    Tainted: P S    VLI
Jun  9 11:35:51 localhost kernel: [4295023.549000] EFLAGS: 00210006   (2.6.15-23-k7) 
Jun  9 11:35:51 localhost kernel: [4295023.549000] EIP is at radix_tree_lookup+0x79/0x90
Jun  9 11:35:51 localhost kernel: [4295023.549000] eax: 48a31a05   ebx: 00000004   ecx: 00000000   edx: 00000004
Jun  9 11:35:51 localhost kernel: [4295023.549000] esi: fffffffa   edi: 01190024   ebp: 48a31971   esp: c95c3be0
Jun  9 11:35:51 localhost kernel: [4295023.549000] ds: 007b   es: 007b   ss: 0068
Jun  9 11:35:51 localhost kernel: [4295023.549000] Process firefox-bin (pid: 5443, threadinfo=c95c2000 task=cf4a1a90)
Jun  9 11:35:51 localhost kernel: [4295023.549000] Stack: db276dd0 db276ddc 00000000 00000000 c014d2dc db276dd0 01190024 db276dcc 
Jun  9 11:35:51 localhost kernel: [4295023.549000]        01190024 c0171d11 db276dcc 01190024 d8477afc deb48e3c deb48170 deb48f40 
Jun  9 11:35:51 localhost kernel: [4295023.549000]        db276d14 c97a09f8 cb1d45b4 00000000 c1488060 c1488060 c148805c c0172f75 
Jun  9 11:35:51 localhost kernel: [4295023.549000] Call Trace:
Jun  9 11:35:51 localhost kernel: [4295023.549000]  [find_get_page+44/96] find_get_page+0x2c/0x60
Jun  9 11:35:51 localhost kernel: [4295023.549000]  [__find_get_block_slow+81/368] __find_get_block_slow+0x51/0x170
Jun  9 11:35:51 localhost kernel: [4295023.549000]  [__find_get_block+245/288] __find_get_block+0xf5/0x120
Jun  9 11:35:51 localhost kernel: [4295023.549000]  [__getblk+55/128] __getblk+0x37/0x80
Jun  9 11:35:51 localhost kernel: [4295023.549000]  [pg0+542878633/1069179904] search_by_key+0x99/0xee0 [reiserfs]
Jun  9 11:35:51 localhost kernel: [4295023.549000]  [ip_output+371/800] ip_output+0x173/0x320
Jun  9 11:35:51 localhost kernel: [4295023.549000]  [activate_task+155/224] activate_task+0x9b/0xe0
Jun  9 11:35:51 localhost kernel: [4295023.549000]  [pg0+548411661/1069179904] _nv001783rm+0x1d/0x2c [nvidia]
Jun  9 11:35:51 localhost kernel: [4295023.549000]  [pg0+548411670/1069179904] _nv001783rm+0x26/0x2c [nvidia]
Jun  9 11:35:51 localhost kernel: [4295023.549000]  [pg0+548411661/1069179904] _nv001783rm+0x1d/0x2c [nvidia]
Jun  9 11:35:51 localhost kernel: [4295023.549000]  [try_to_wake_up+140/1040] try_to_wake_up+0x8c/0x410
Jun  9 11:35:51 localhost kernel: [4295023.549000]  [pg0+549644455/1069179904] _nv004205rm+0xa7/0xe8 [nvidia]
Jun  9 11:35:51 localhost kernel: [4295023.549000]  [in_group_p+67/144] in_group_p+0x43/0x90
Jun  9 11:35:51 localhost kernel: [4295023.549000]  [pg0+542764439/1069179904] search_by_entry_key+0x37/0x250 [reiserfs]
Jun  9 11:35:51 localhost kernel: [4295023.549000]  [pg0+542766057/1069179904] reiserfs_find_entry+0xb9/0x140 [reiserfs]
Jun  9 11:35:51 localhost kernel: [4295023.549000]  [pg0+542766367/1069179904] reiserfs_lookup+0xaf/0x1a0 [reiserfs]
Jun  9 11:35:51 localhost kernel: [4295023.549000]  [dput+242/528] dput+0xf2/0x210
Jun  9 11:35:51 localhost kernel: [4295023.549000]  [mntput_no_expire+28/144] mntput_no_expire+0x1c/0x90
Jun  9 11:35:51 localhost kernel: [4295023.549000]  [link_path_walk+127/256] link_path_walk+0x7f/0x100
Jun  9 11:35:51 localhost kernel: [4295023.549000]  [__lookup_hash+191/224] __lookup_hash+0xbf/0xe0
Jun  9 11:35:51 localhost kernel: [4295023.549000]  [lookup_hash+28/32] lookup_hash+0x1c/0x20
Jun  9 11:35:51 localhost kernel: [4295023.549000]  [open_namei+281/1728] open_namei+0x119/0x6c0
Jun  9 11:35:51 localhost kernel: [4295023.549000]  [sock_poll+32/48] sock_poll+0x20/0x30
Jun  9 11:35:51 localhost kernel: [4295023.549000]  [filp_open+56/96] filp_open+0x38/0x60
Jun  9 11:35:51 localhost kernel: [4295023.549000]  [get_unused_fd+186/224] get_unused_fd+0xba/0xe0
Jun  9 11:35:51 localhost kernel: [4295023.549000]  [do_sys_open+85/256] do_sys_open+0x55/0x100
Jun  9 11:35:51 localhost kernel: [4295023.549000]  [sysenter_past_esp+84/117] sysenter_past_esp+0x54/0x75
Jun  9 11:35:51 localhost kernel: [4295023.549000] Code: 83 e0 3f 39 d3 8d 44 85 04 74 1c 8b 28 42 85 ed 75 e5 8b 1c 24 8b 74 24 04 31 c0 8b 7c 24 08 8b 6c 24 0c 83 c4 10 c3 85 c0 74 e7 <8b> 00 8b 1c 24 8b 74 24 04 8b 7c 24 08 8b 6c 24 0c 83 c4 10 c3 
Jun  9 11:35:51 localhost kernel: [4295023.549000]  <6>note: firefox-bin[5443] exited with preempt_count 1

Jun  9 12:01:38 localhost kernel: [ 1503.328920] Unable to handle kernel paging request at virtual address 80936404
Jun  9 12:01:38 localhost kernel: [ 1503.328933]  printing eip:
Jun  9 12:01:38 localhost kernel: [ 1503.328936] c01732d1
Jun  9 12:01:38 localhost kernel: [ 1503.328939] *pde = 00000000
Jun  9 12:01:38 localhost kernel: [ 1503.328943] Oops: 0000 [#1]
Jun  9 12:01:38 localhost kernel: [ 1503.328946] PREEMPT SMP 
Jun  9 12:01:38 localhost kernel: [ 1503.328950] Modules linked in: binfmt_misc ipt_TCPMSS ipt_limit ip_nat_irc ip_nat_ftp iptable_nat iptable_mangle ipt_LOG ipt_MASQUERADE ip_nat ipt_TOS ipt_REJECT ip_conntrack_irc ip_conntrack_ftp ipt_state ip_conntrack nfnetlink iptable_filter ip_tables apm nls_iso8859_1 nls_cp437 vfat fat ext3 jbd ipv6 dm_mod md_mod af_packet sr_mod sbp2 scsi_mod lp rsrc_nonstatic pcmcia_core tsdev serio_raw pcspkr snd_emu10k1_synth snd_emux_synth snd_seq_virmidi snd_seq_midi_emul snd_seq_dummy snd_seq_oss snd_seq_midi snd_seq_midi_event psmouse floppy snd_seq snd_emu10k1 snd_rawmidi snd_ac97_codec snd_ac97_bus snd_pcm_oss i2c_viapro via686a i2c_isa snd_mixer_oss snd_pcm snd_seq_device snd_timer snd_page_alloc snd_util_mem snd_hwdep nvidia i2c_core snd soundcore 8139too 8139cp mii emu10k1_gp gameport parport_pc parport shpchp pci_hotplug via_agp agpgart evdev reiserfs ide_generic ohci1394 ieee1394 uhci_hcd ehci_hcd ohci_hcd usbcore hpt366 ide_disk ide_cd cdrom generic via82cxxx processor capab
Jun  9 12:01:38 localhost kernel: lity commoncap vga16fb vgastate fbcon tileblit font bitblit softcursor
Jun  9 12:01:38 localhost kernel: [ 1503.329027] CPU:    0
Jun  9 12:01:38 localhost kernel: [ 1503.329029] EIP:    0060:[block_invalidatepage+129/224]    Tainted: P S    VLI
Jun  9 12:01:38 localhost kernel: [ 1503.329031] EFLAGS: 00210212   (2.6.15-23-k7) 
Jun  9 12:01:38 localhost kernel: [ 1503.329049] EIP is at block_invalidatepage+0x81/0xe0
Jun  9 12:01:38 localhost kernel: [ 1503.329054] eax: 769e693d   ebx: 809363f4   ecx: 00000002   edx: d86a6170
Jun  9 12:01:38 localhost kernel: [ 1503.329060] esi: 809363f4   edi: 769e693d   ebp: d86a6170   esp: d8303e90
Jun  9 12:01:38 localhost kernel: [ 1503.329064] ds: 007b   es: 007b   ss: 0068
Jun  9 12:01:38 localhost kernel: [ 1503.329069] Process mv (pid: 6429, threadinfo=d8302000 task=d133aab0)
Jun  9 12:01:38 localhost kernel: [ 1503.329072] Stack: 00000000 c115a4e8 c115a4e8 00006ea8 c115a4e8 d8303edc c0159374 c115a4e8 
Jun  9 12:01:38 localhost kernel: [ 1503.329083]        00000000 00000000 c0159501 d693ad58 c115a4e8 00000000 0000000e 00000000 
Jun  9 12:01:38 localhost kernel: [ 1503.329091]        00001000 00000000 00000000 0000000e 00000000 c115a4e8 c138f97c c14013c4 
Jun  9 12:01:38 localhost kernel: [ 1503.329100] Call Trace:
Jun  9 12:01:38 localhost kernel: [ 1503.329126]  [truncate_complete_page+84/96] truncate_complete_page+0x54/0x60
Jun  9 12:01:38 localhost kernel: [ 1503.329144]  [truncate_inode_pages+193/688] truncate_inode_pages+0xc1/0x2b0
Jun  9 12:01:38 localhost kernel: [ 1503.329186]  [pg0+547710224/1069179904] fat_delete_inode+0x0/0x60 [fat]
Jun  9 12:01:38 localhost kernel: [ 1503.329221]  [pg0+547710262/1069179904] fat_delete_inode+0x26/0x60 [fat]
Jun  9 12:01:38 localhost kernel: [ 1503.329241]  [generic_delete_inode+132/336] generic_delete_inode+0x84/0x150
Jun  9 12:01:38 localhost kernel: [ 1503.329255]  [iput+65/128] iput+0x41/0x80
Jun  9 12:01:38 localhost kernel: [ 1503.329265]  [sys_unlink+257/304] sys_unlink+0x101/0x130
Jun  9 12:01:38 localhost kernel: [ 1503.329307]  [sysenter_past_esp+84/117] sysenter_past_esp+0x54/0x75
Jun  9 12:01:38 localhost kernel: [ 1503.329339] Code: 43 20 00 00 00 00 90 0f ba 33 05 90 0f ba 33 03 90 0f ba 33 06 90 0f ba 33 09 89 d8 e8 e9 e2 ff ff 39 f5 89 f3 89 f8 74 23 89 c7 <03> 7b 10 3b 04 24 8b 73 04 72 eb 90 0f ba 2b 02 19 c0 85 c0 74 

```

---

### Post by sswords on 2006-06-11
Update:  I reinstalled Dapper from scratch and have been using the open-source nv drivers instead of nvidia-legacy as well as the generic 386 Ubuntu kernel rather than k7.  Things seem somewhat more stable but I just got a bunch of oopses, again with "Unable to handle kernel paging request."  There were a few I didn't notice, but then firefox started crashing so I checked kern.log and found the messages.  If anyone has any experience with this sort of thing, please help me out; I think my next step is to compile a new kernel if it keeps up.

One thing I'm suspicious about is the number of modules loaded.  In particular, nvidia is loaded even though I'm using the nv driver. Does anyone have guidance on which ones could be disabled (and how to do that?)

Here are the new log files:
```
Jun 11 02:35:46 insanitysauce kernel: [4298806.786000] Unable to handle kernel paging request at virtual address 6d6f7266
Jun 11 02:35:46 insanitysauce kernel: [4298806.786000]  printing eip:
Jun 11 02:35:46 insanitysauce kernel: [4298806.786000] c017b68c
Jun 11 02:35:46 insanitysauce kernel: [4298806.786000] *pde = 00000000
Jun 11 02:35:46 insanitysauce kernel: [4298806.786000] Oops: 0002 [#1]
Jun 11 02:35:46 insanitysauce kernel: [4298806.786000] PREEMPT 
Jun 11 02:35:46 insanitysauce kernel: [4298806.786000] Modules linked in: isofs nls_utf8 udf rfcomm l2cap bluetooth ppdev tc1100_wmi video acpi_sbs battery i2c_acpi_ec container button pcc_acpi sony_acpi ac dev_acpi hotkey nls_iso8859_1 nls_cp437 vfat fat ext3 jbd ipv6 dm_mod md_mod af_packet sr_mod sbp2 scsi_mod lp tsdev floppy snd_emu10k1_synth snd_emux_synth snd_seq_virmidi snd_seq_midi_emul snd_seq_dummy snd_seq_oss snd_seq_midi snd_seq_midi_event snd_seq snd_emu10k1 snd_rawmidi snd_ac97_codec snd_ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_device snd_timer snd_page_alloc snd_util_mem pcspkr snd_hwdep snd nvidia rtc psmouse serio_raw soundcore emu10k1_gp gameport 8139too 8139cp mii i2c_viapro via686a i2c_isa via_agp i2c_core shpchp pci_hotplug parport_pc parport agpgart evdev reiserfs ide_generic ehci_hcd ohci1394 ieee1394 ohci_hcd uhci_hcd usbcore hpt366 ide_disk ide_cd cdrom generic via82cxxx thermal processor fan fbcon tileblit font bitblit softcursor capability commoncap
Jun 11 02:35:46 insanitysauce kernel: [4298806.786000] CPU:    0
Jun 11 02:35:46 insanitysauce kernel: [4298806.786000] EIP:    0060:[generic_forget_inode+92/416]    Tainted: P      VLI
Jun 11 02:35:46 insanitysauce kernel: [4298806.786000] EFLAGS: 00210246   (2.6.15-23-386) 
Jun 11 02:35:46 insanitysauce kernel: [4298806.786000] EIP is at generic_forget_inode+0x5c/0x1a0
Jun 11 02:35:46 insanitysauce kernel: [4298806.786000] eax: 6d6f7266   ebx: da0b3860   ecx: d3edf868   edx: da0b3868
Jun 11 02:35:47 insanitysauce kernel: [4298806.786000] esi: dfdade00   edi: dfe2e000   ebp: dfe2e000   esp: dfe2fed8
Jun 11 02:35:47 insanitysauce kernel: [4298806.786000] ds: 007b   es: 007b   ss: 0068
Jun 11 02:35:47 insanitysauce kernel: [4298806.786000] Process kswapd0 (pid: 110, threadinfo=dfe2e000 task=de8a1550)
Jun 11 02:35:47 insanitysauce kernel: [4298806.786000] Stack: c15ac5e0 da0b3860 c0178736 da0b3860 dfe2e000 00000080 dfe2e000 00000040 
Jun 11 02:35:47 insanitysauce kernel: [4298806.786000]        00001af4 dffeeaa0 00000080 0001cac6 c0178cb0 00000080 c014b1a7 00000080 
Jun 11 02:35:47 insanitysauce kernel: [4298806.786000]        000000d0 00000000 000000d0 00000003 00000000 00000000 00000080 c0338340 
Jun 11 02:35:47 insanitysauce kernel: [4298806.786000] Call Trace:
Jun 11 02:35:47 insanitysauce kernel: [4298806.786000]  [prune_dcache+502/624] prune_dcache+0x1f6/0x270
Jun 11 02:35:47 insanitysauce kernel: [4298806.786000]  [shrink_dcache_memory+64/80] shrink_dcache_memory+0x40/0x50
Jun 11 02:35:47 insanitysauce kernel: [4298806.786000]  [shrink_slab+279/432] shrink_slab+0x117/0x1b0
Jun 11 02:35:47 insanitysauce kernel: [4298806.786000]  [balance_pgdat+688/1040] balance_pgdat+0x2b0/0x410
Jun 11 02:35:47 insanitysauce kernel: [4298806.786000]  [kswapd+198/272] kswapd+0xc6/0x110
Jun 11 02:35:47 insanitysauce kernel: [4298806.786000]  [autoremove_wake_function+0/64] autoremove_wake_function+0x0/0x40
Jun 11 02:35:47 insanitysauce kernel: [4298806.786000]  [kswapd+0/272] kswapd+0x0/0x110
Jun 11 02:35:47 insanitysauce kernel: [4298806.786000]  [kernel_thread_helper+5/16] kernel_thread_helper+0x5/0x10
Jun 11 02:35:47 insanitysauce kernel: [4298806.786000] Code: 00 e0 ff ff 21 e0 ff 48 14 8b 40 08 a8 08 0f 85 37 01 00 00 5b 5e c3 90 8d b4 26 00 00 00 00 8d 53 08 8b 4b 08 8b 42 04 89 41 04 <89> 08 a1 ac 95 33 c0 89 50 04 89 43 08 c7 42 04 ac 95 33 c0 89 
Jun 11 02:35:47 insanitysauce kernel: [4298806.786000]  <6>note: kswapd0[110] exited with preempt_count 1


Jun 11 02:36:03 insanitysauce kernel: [4298824.401000] Unable to handle kernel paging request at virtual address 47203659
Jun 11 02:36:03 insanitysauce kernel: [4298824.401000]  printing eip:
Jun 11 02:36:03 insanitysauce kernel: [4298824.401000] c017b7ff
Jun 11 02:36:03 insanitysauce kernel: [4298824.401000] *pde = 00000000
Jun 11 02:36:03 insanitysauce kernel: [4298824.401000] Oops: 0000 [#2]
Jun 11 02:36:03 insanitysauce kernel: [4298824.401000] PREEMPT 
Jun 11 02:36:03 insanitysauce kernel: [4298824.401000] Modules linked in: isofs nls_utf8 udf rfcomm l2cap bluetooth ppdev tc1100_wmi video acpi_sbs battery i2c_acpi_ec container button pcc_acpi sony_acpi ac dev_acpi hotkey nls_iso8859_1 nls_cp437 vfat fat ext3 jbd ipv6 dm_mod md_mod af_packet sr_mod sbp2 scsi_mod lp tsdev floppy snd_emu10k1_synth snd_emux_synth snd_seq_virmidi snd_seq_midi_emul snd_seq_dummy snd_seq_oss snd_seq_midi snd_seq_midi_event snd_seq snd_emu10k1 snd_rawmidi snd_ac97_codec snd_ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_device snd_timer snd_page_alloc snd_util_mem pcspkr snd_hwdep snd nvidia rtc psmouse serio_raw soundcore emu10k1_gp gameport 8139too 8139cp mii i2c_viapro via686a i2c_isa via_agp i2c_core shpchp pci_hotplug parport_pc parport agpgart evdev reiserfs ide_generic ehci_hcd ohci1394 ieee1394 ohci_hcd uhci_hcd usbcore hpt366 ide_disk ide_cd cdrom generic via82cxxx thermal processor fan fbcon tileblit font bitblit softcursor capability commoncap
Jun 11 02:36:03 insanitysauce kernel: [4298824.401000] CPU:    0
Jun 11 02:36:03 insanitysauce kernel: [4298824.401000] EIP:    0060:[iput+15/144]    Tainted: P      VLI
Jun 11 02:36:03 insanitysauce kernel: [4298824.401000] EFLAGS: 00010282   (2.6.15-23-386) 
Jun 11 02:36:03 insanitysauce kernel: [4298824.401000] EIP is at iput+0xf/0x90
Jun 11 02:36:03 insanitysauce kernel: [4298824.401000] eax: 47203635   ebx: da0b36d0   ecx: ee5b64e9   edx: da0b36e8
Jun 11 02:36:03 insanitysauce kernel: [4298824.401000] esi: da0b36d0   edi: c72e2000   ebp: c72e2000   esp: c72e3c34
Jun 11 02:36:03 insanitysauce kernel: [4298824.401000] ds: 007b   es: 007b   ss: 0068
Jun 11 02:36:03 insanitysauce kernel: [4298824.401000] Process hald-addon-stor (pid: 4682, threadinfo=c72e2000 task=c7235a90)
Jun 11 02:36:03 insanitysauce kernel: [4298824.401000] Stack: c15ac3c0 c0178736 da0b36d0 c72e2000 00000080 c72e2000 00000000 00001a90 
Jun 11 02:36:03 insanitysauce kernel: [4298824.401000]        dffeeaa0 00000082 0001ca90 c0178cb0 00000080 c014b1a7 00000080 000280d2 
Jun 11 02:36:03 insanitysauce kernel: [4298824.401000]        00000000 000280d2 00000003 00000000 00000000 00000080 0000000a c72e3d14 
Jun 11 02:36:03 insanitysauce kernel: [4298824.401000] Call Trace:
Jun 11 02:36:03 insanitysauce kernel: [4298824.401000]  [prune_dcache+502/624] prune_dcache+0x1f6/0x270
Jun 11 02:36:03 insanitysauce kernel: [4298824.401000]  [shrink_dcache_memory+64/80] shrink_dcache_memory+0x40/0x50
Jun 11 02:36:03 insanitysauce kernel: [4298824.401000]  [shrink_slab+279/432] shrink_slab+0x117/0x1b0
Jun 11 02:36:03 insanitysauce kernel: [4298824.401000]  [try_to_free_pages+195/480] try_to_free_pages+0xc3/0x1e0
Jun 11 02:36:03 insanitysauce kernel: [4298824.401000]  [__alloc_pages+356/736] __alloc_pages+0x164/0x2e0
Jun 11 02:36:03 insanitysauce kernel: [4298824.401000]  [do_anonymous_page+204/400] do_anonymous_page+0xcc/0x190
Jun 11 02:36:03 insanitysauce kernel: [4298824.401000]  [__handle_mm_fault+407/528] __handle_mm_fault+0x197/0x210
Jun 11 02:36:03 insanitysauce kernel: [4298824.401000]  [do_page_fault+534/1562] do_page_fault+0x216/0x61a
Jun 11 02:36:03 insanitysauce kernel: [4298824.401000]  [do_page_fault+0/1562] do_page_fault+0x0/0x61a
Jun 11 02:36:03 insanitysauce kernel: [4298824.401000]  [error_code+79/96] error_code+0x4f/0x60
Jun 11 02:36:03 insanitysauce kernel: [4298824.401000]  [file_read_actor+30/192] file_read_actor+0x1e/0xc0
Jun 11 02:36:03 insanitysauce kernel: [4298824.401000]  [do_generic_mapping_read+855/1248] do_generic_mapping_read+0x357/0x4e0
Jun 11 02:36:03 insanitysauce kernel: [4298824.401000]  [__generic_file_aio_read+155/560] __generic_file_aio_read+0x9b/0x230
Jun 11 02:36:03 insanitysauce kernel: [4298824.401000]  [file_read_actor+0/192] file_read_actor+0x0/0xc0
Jun 11 02:36:03 insanitysauce kernel: [4298824.401000]  [generic_file_read+166/208] generic_file_read+0xa6/0xd0
Jun 11 02:36:03 insanitysauce kernel: [4298824.401000]  [vma_link+87/320] vma_link+0x57/0x140
Jun 11 02:36:03 insanitysauce kernel: [4298824.401000]  [do_mmap_pgoff+1256/1904] do_mmap_pgoff+0x4e8/0x770
Jun 11 02:36:03 insanitysauce kernel: [4298824.401000]  [autoremove_wake_function+0/64] autoremove_wake_function+0x0/0x40
Jun 11 02:36:03 insanitysauce kernel: [4298824.401000]  [vfs_read+150/336] vfs_read+0x96/0x150
Jun 11 02:36:03 insanitysauce kernel: [4298824.401000]  [sys_read+56/128] sys_read+0x38/0x80
Jun 11 02:36:03 insanitysauce kernel: [4298824.401000]  [sysenter_past_esp+84/121] sysenter_past_esp+0x54/0x79
Jun 11 02:36:03 insanitysauce kernel: [4298824.401000] Code: 8b 50 2c 85 d2 75 05 e9 f0 fc ff ff 89 44 24 04 e9 47 fe ff ff 8d b4 26 00 00 00 00 53 8b 5c 24 08 85 db 74 57 8b 83 94 00 00 00 <8b> 40 24 83 bb 2c 01 00 00 20 74 61 85 c0 74 0b 8b 40 14 85 c0 


Jun 11 03:14:52 insanitysauce kernel: [4298824.401000]  <1>Unable to handle kernel paging request at virtual address 6d6f7266
Jun 11 03:14:52 insanitysauce kernel: [4301153.582000]  printing eip:
Jun 11 03:14:52 insanitysauce kernel: [4301153.582000] c017b68c
Jun 11 03:14:52 insanitysauce kernel: [4301153.582000] *pde = 00000000
Jun 11 03:14:52 insanitysauce kernel: [4301153.582000] Oops: 0002 [#3]
Jun 11 03:14:52 insanitysauce kernel: [4301153.582000] PREEMPT 
Jun 11 03:14:52 insanitysauce kernel: [4301153.582000] Modules linked in: isofs nls_utf8 udf rfcomm l2cap bluetooth ppdev tc1100_wmi video acpi_sbs battery i2c_acpi_ec container button pcc_acpi sony_acpi ac dev_acpi hotkey nls_iso8859_1 nls_cp437 vfat fat ext3 jbd ipv6 dm_mod md_mod af_packet sr_mod sbp2 scsi_mod lp tsdev floppy snd_emu10k1_synth snd_emux_synth snd_seq_virmidi snd_seq_midi_emul snd_seq_dummy snd_seq_oss snd_seq_midi snd_seq_midi_event snd_seq snd_emu10k1 snd_rawmidi snd_ac97_codec snd_ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_device snd_timer snd_page_alloc snd_util_mem pcspkr snd_hwdep snd nvidia rtc psmouse serio_raw soundcore emu10k1_gp gameport 8139too 8139cp mii i2c_viapro via686a i2c_isa via_agp i2c_core shpchp pci_hotplug parport_pc parport agpgart evdev reiserfs ide_generic ehci_hcd ohci1394 ieee1394 ohci_hcd uhci_hcd usbcore hpt366 ide_disk ide_cd cdrom generic via82cxxx thermal processor fan fbcon tileblit font bitblit softcursor capability commoncap
Jun 11 03:14:52 insanitysauce kernel: [4301153.582000] CPU:    0
Jun 11 03:14:52 insanitysauce kernel: [4301153.582000] EIP:    0060:[generic_forget_inode+92/416]    Tainted: P      VLI
Jun 11 03:14:52 insanitysauce kernel: [4301153.582000] EFLAGS: 00010246   (2.6.15-23-386) 
Jun 11 03:14:52 insanitysauce kernel: [4301153.582000] EIP is at generic_forget_inode+0x5c/0x1a0
Jun 11 03:14:52 insanitysauce kernel: [4301153.582000] eax: 6d6f7266   ebx: d3edf860   ecx: d3edf548   edx: d3edf868
Jun 11 03:14:52 insanitysauce kernel: [4301153.582000] esi: db7e5200   edi: d1892000   ebp: d1892000   esp: d1893e34
Jun 11 03:14:52 insanitysauce kernel: [4301153.582000] ds: 007b   es: 007b   ss: 0068
Jun 11 03:14:52 insanitysauce kernel: [4301153.582000] Process nautilus (pid: 4947, threadinfo=d1892000 task=d24f6570)
Jun 11 03:14:52 insanitysauce kernel: [4301153.582000] Stack: d2120090 d3edf860 c0178736 d3edf860 d1892000 00000080 d1892000 0000005e 
Jun 11 03:14:52 insanitysauce kernel: [4301153.582000]        00003e80 dffeeaa0 00000095 0001ccdf c0178cb0 00000080 c014b1a7 00000080 
Jun 11 03:14:52 insanitysauce kernel: [4301153.582000]        000280d2 00000000 000280d2 00000016 00000000 00000000 00000148 00000009 
Jun 11 03:14:52 insanitysauce kernel: [4301153.582000] Call Trace:
Jun 11 03:14:52 insanitysauce kernel: [4301153.582000]  [prune_dcache+502/624] prune_dcache+0x1f6/0x270
Jun 11 03:14:52 insanitysauce kernel: [4301153.582000]  [shrink_dcache_memory+64/80] shrink_dcache_memory+0x40/0x50
Jun 11 03:14:52 insanitysauce kernel: [4301153.582000]  [shrink_slab+279/432] shrink_slab+0x117/0x1b0
Jun 11 03:14:52 insanitysauce kernel: [4301153.582000]  [try_to_free_pages+195/480] try_to_free_pages+0xc3/0x1e0
Jun 11 03:14:52 insanitysauce kernel: [4301153.582000]  [__alloc_pages+356/736] __alloc_pages+0x164/0x2e0
Jun 11 03:14:52 insanitysauce kernel: [4301153.582000]  [do_anonymous_page+204/400] do_anonymous_page+0xcc/0x190
Jun 11 03:14:52 insanitysauce kernel: [4301153.582000]  [__handle_mm_fault+407/528] __handle_mm_fault+0x197/0x210
Jun 11 03:14:52 insanitysauce kernel: [4301153.582000]  [do_page_fault+534/1562] do_page_fault+0x216/0x61a
Jun 11 03:14:52 insanitysauce kernel: [4301153.582000]  [do_page_fault+0/1562] do_page_fault+0x0/0x61a
Jun 11 03:14:52 insanitysauce kernel: [4301153.582000]  [error_code+79/96] error_code+0x4f/0x60
Jun 11 03:14:52 insanitysauce kernel: [4301153.582000] Code: 00 e0 ff ff 21 e0 ff 48 14 8b 40 08 a8 08 0f 85 37 01 00 00 5b 5e c3 90 8d b4 26 00 00 00 00 8d 53 08 8b 4b 08 8b 42 04 89 41 04 <89> 08 a1 ac 95 33 c0 89 50 04 89 43 08 c7 42 04 ac 95 33 c0 89 
Jun 11 03:14:52 insanitysauce kernel: [4301153.582000]  <6>note: nautilus[4947] exited with preempt_count 1


Jun 11 14:58:50 insanitysauce kernel: [4361641.174000] Unable to handle kernel paging request at virtual address 57f0fb08
Jun 11 14:58:51 insanitysauce kernel: [4361641.174000]  printing eip:
Jun 11 14:58:51 insanitysauce kernel: [4361641.174000] c017b8bf
Jun 11 14:58:51 insanitysauce kernel: [4361641.174000] *pde = 00000000
Jun 11 14:58:51 insanitysauce kernel: [4361641.174000] Oops: 0000 [#4]
Jun 11 14:58:51 insanitysauce kernel: [4361641.174000] PREEMPT 
Jun 11 14:58:51 insanitysauce kernel: [4361641.174000] Modules linked in: isofs nls_utf8 udf rfcomm l2cap bluetooth ppdev tc1100_wmi video acpi_sbs battery i2c_acpi_ec container button pcc_acpi sony_acpi ac dev_acpi hotkey nls_iso8859_1 nls_cp437 vfat fat ext3 jbd ipv6 dm_mod md_mod af_packet sr_mod sbp2 scsi_mod lp tsdev floppy snd_emu10k1_synth snd_emux_synth snd_seq_virmidi snd_seq_midi_emul snd_seq_dummy snd_seq_oss snd_seq_midi snd_seq_midi_event snd_seq snd_emu10k1 snd_rawmidi snd_ac97_codec snd_ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_device snd_timer snd_page_alloc snd_util_mem pcspkr snd_hwdep snd nvidia rtc psmouse serio_raw soundcore emu10k1_gp gameport 8139too 8139cp mii i2c_viapro via686a i2c_isa via_agp i2c_core shpchp pci_hotplug parport_pc parport agpgart evdev reiserfs ide_generic ehci_hcd ohci1394 ieee1394 ohci_hcd uhci_hcd usbcore hpt366 ide_disk ide_cd cdrom generic via82cxxx thermal processor fan fbcon tileblit font bitblit softcursor capability commoncap
Jun 11 14:58:51 insanitysauce kernel: [4361641.174000] CPU:    0
Jun 11 14:58:51 insanitysauce kernel: [4361641.174000] EIP:    0060:[update_atime+15/144]    Tainted: P      VLI
Jun 11 14:58:51 insanitysauce kernel: [4361641.174000] EFLAGS: 00210296   (2.6.15-23-386) 
Jun 11 14:58:51 insanitysauce kernel: [4361641.174000] EIP is at update_atime+0xf/0x90
Jun 11 14:58:51 insanitysauce kernel: [4361641.174000] eax: d3689570   ebx: da0b3220   ecx: 57f0fad4   edx: ca0f1118
Jun 11 14:58:51 insanitysauce kernel: [4361641.174000] esi: ca0f1118   edi: c232df18   ebp: ca0f1118   esp: c232de28
Jun 11 14:58:51 insanitysauce kernel: [4361641.174000] ds: 007b   es: 007b   ss: 0068
Jun 11 14:58:51 insanitysauce kernel: [4361641.174000] Process firefox-bin (pid: 19593, threadinfo=c232c000 task=d3689570)
Jun 11 14:58:51 insanitysauce kernel: [4361641.174000] Stack: aff08e97 c56673b0 da0b3220 ca0f1118 c016ef06 da0b3220 c232c000 c232c000 
Jun 11 14:58:51 insanitysauce kernel: [4361641.174000]        c232c000 c232c000 c232c000 c232c000 c232df18 db69101c 00000000 00000001 
Jun 11 14:58:51 insanitysauce kernel: [4361641.174000]        c232c000 dfb3d6f0 c0177fed aff08e97 0000000d db69101c dffe4ea0 ca0f1118 
Jun 11 14:58:51 insanitysauce kernel: [4361641.174000] Call Trace:
Jun 11 14:58:51 insanitysauce kernel: [4361641.174000]  [__link_path_walk+3430/4064] __link_path_walk+0xd66/0xfe0
Jun 11 14:58:51 insanitysauce kernel: [4361641.174000]  [dput+269/704] dput+0x10d/0x2c0
Jun 11 14:58:51 insanitysauce kernel: [4361641.174000]  [link_path_walk+69/208] link_path_walk+0x45/0xd0
Jun 11 14:58:51 insanitysauce kernel: [4361641.174000]  [path_lookup+131/352] path_lookup+0x83/0x160
Jun 11 14:58:51 insanitysauce kernel: [4361641.174000]  [__user_walk+35/64] __user_walk+0x23/0x40
Jun 11 14:58:51 insanitysauce kernel: [4361641.174000]  [vfs_stat+23/80] vfs_stat+0x17/0x50
Jun 11 14:58:51 insanitysauce kernel: [4361641.174000]  [sys_stat64+17/64] sys_stat64+0x11/0x40
Jun 11 14:58:51 insanitysauce kernel: [4361641.174000]  [sysenter_past_esp+84/121] sysenter_past_esp+0x54/0x79
Jun 11 14:58:51 insanitysauce kernel: [4361641.174000] Code: 0b 89 5c 24 08 5b ff e0 8d 74 26 00 31 c0 31 d2 5b c3 8d 76 00 8d bc 27 00 00 00 00 56 53 83 ec 08 8b 5c 24 14 8b 8b 94 00 00 00 <8b> 51 34 f6 c6 04 75 29 f6 83 34 01 00 00 02 75 20 f6 c6 08 74 


Jun 11 15:00:14 insanitysauce kernel: [4361641.174000]  <1>Unable to handle kernel paging request at virtual address 57f0fb08
Jun 11 15:00:14 insanitysauce kernel: [4361724.936000]  printing eip:
Jun 11 15:00:14 insanitysauce kernel: [4361724.936000] c017b8bf
Jun 11 15:00:14 insanitysauce kernel: [4361724.936000] *pde = 00000000
Jun 11 15:00:14 insanitysauce kernel: [4361724.936000] Oops: 0000 [#5]
Jun 11 15:00:14 insanitysauce kernel: [4361724.936000] PREEMPT 
Jun 11 15:00:14 insanitysauce kernel: [4361724.936000] Modules linked in: isofs nls_utf8 udf rfcomm l2cap bluetooth ppdev tc1100_wmi video acpi_sbs battery i2c_acpi_ec container button pcc_acpi sony_acpi ac dev_acpi hotkey nls_iso8859_1 nls_cp437 vfat fat ext3 jbd ipv6 dm_mod md_mod af_packet sr_mod sbp2 scsi_mod lp tsdev floppy snd_emu10k1_synth snd_emux_synth snd_seq_virmidi snd_seq_midi_emul snd_seq_dummy snd_seq_oss snd_seq_midi snd_seq_midi_event snd_seq snd_emu10k1 snd_rawmidi snd_ac97_codec snd_ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_device snd_timer snd_page_alloc snd_util_mem pcspkr snd_hwdep snd nvidia rtc psmouse serio_raw soundcore emu10k1_gp gameport 8139too 8139cp mii i2c_viapro via686a i2c_isa via_agp i2c_core shpchp pci_hotplug parport_pc parport agpgart evdev reiserfs ide_generic ehci_hcd ohci1394 ieee1394 ohci_hcd uhci_hcd usbcore hpt366 ide_disk ide_cd cdrom generic via82cxxx thermal processor fan fbcon tileblit font bitblit softcursor capability commoncap
Jun 11 15:00:14 insanitysauce kernel: [4361724.936000] CPU:    0
Jun 11 15:00:14 insanitysauce kernel: [4361724.936000] EIP:    0060:[update_atime+15/144]    Tainted: P      VLI
Jun 11 15:00:14 insanitysauce kernel: [4361724.936000] EFLAGS: 00210296   (2.6.15-23-386) 
Jun 11 15:00:14 insanitysauce kernel: [4361724.936000] EIP is at update_atime+0xf/0x90
Jun 11 15:00:14 insanitysauce kernel: [4361724.936000] eax: d3689570   ebx: da0b3220   ecx: 57f0fad4   edx: ca0f1118
Jun 11 15:00:14 insanitysauce kernel: [4361724.936000] esi: ca0f1118   edi: c232df18   ebp: ca0f1118   esp: c232de28
Jun 11 15:00:14 insanitysauce kernel: [4361724.936000] ds: 007b   es: 007b   ss: 0068
Jun 11 15:00:14 insanitysauce kernel: [4361724.936000] Process firefox-bin (pid: 7889, threadinfo=c232c000 task=d3689570)
Jun 11 15:00:14 insanitysauce kernel: [4361724.936000] Stack: aff08e97 c56673b0 da0b3220 ca0f1118 c016ef06 da0b3220 c232c000 c232c000 
Jun 11 15:00:14 insanitysauce kernel: [4361724.936000]        c232c000 c232c000 c232c000 c232c000 c232df18 dfef901c 00000000 00000001 
Jun 11 15:00:14 insanitysauce kernel: [4361724.936000]        c232c000 dfb3d6f0 c0177fed aff08e97 0000000d dfef901c dffe4ea0 ca0f1118 
Jun 11 15:00:14 insanitysauce kernel: [4361724.936000] Call Trace:
Jun 11 15:00:14 insanitysauce kernel: [4361724.936000]  [__link_path_walk+3430/4064] __link_path_walk+0xd66/0xfe0
Jun 11 15:00:14 insanitysauce kernel: [4361724.936000]  [dput+269/704] dput+0x10d/0x2c0
Jun 11 15:00:14 insanitysauce kernel: [4361724.936000]  [link_path_walk+69/208] link_path_walk+0x45/0xd0
Jun 11 15:00:14 insanitysauce kernel: [4361724.936000]  [path_lookup+131/352] path_lookup+0x83/0x160
Jun 11 15:00:14 insanitysauce kernel: [4361724.936000]  [__user_walk+35/64] __user_walk+0x23/0x40
Jun 11 15:00:14 insanitysauce kernel: [4361724.936000]  [vfs_stat+23/80] vfs_stat+0x17/0x50
Jun 11 15:00:14 insanitysauce kernel: [4361724.936000]  [sys_stat64+17/64] sys_stat64+0x11/0x40
Jun 11 15:00:14 insanitysauce kernel: [4361724.936000]  [sys_init_module+116/464] sys_init_module+0x74/0x1d0
Jun 11 15:00:14 insanitysauce kernel: [4361724.936000]  [sysenter_past_esp+84/121] sysenter_past_esp+0x54/0x79
Jun 11 15:00:14 insanitysauce kernel: [4361724.936000] Code: 0b 89 5c 24 08 5b ff e0 8d 74 26 00 31 c0 31 d2 5b c3 8d 76 00 8d bc 27 00 00 00 00 56 53 83 ec 08 8b 5c 24 14 8b 8b 94 00 00 00 <8b> 51 34 f6 c6 04 75 29 f6 83 34 01 00 00 02 75 20 f6 c6 08 74 

```

---

### Post by yaztromo on 2006-06-11
I don't really know what it could be if it's a software fault. But have you tried testing for bad ram/cpu. Run memtext86 for a few hours to eliminate a possible ram problem.

---

### Post by sswords on 2006-06-13
Well, I compiled my own kernel as described [here]("http://ubuntuforums.org/showthread.php?t=157560") and things seem good so far.  I was pretty sure it wasn't the memory since I tested when this was happening before and it seemed fine.  I'm thinking some module I didn't need was being loaded and making things unstable.

---

