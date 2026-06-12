---
title: "BUG: unable to handle kernel paging request at xxx"
date: 2009-05-18
forum: General Help
---

### Post by Vitani on 2009-05-18
Good afternoon.

Recently my Mythbuntu (9.04) server seems to be becomin[FONT=Tahoma][SIZE=2]g rather u[/SIZE][/FONT]nstable. Looking in /var/log/syslog I see the following lines appearing every time to server starts becoming a problem.
May 15 18:35:48 Phoenix kernel: [449670.170353] BUG: unable to handle kernel paging request at b625e08a
May 15 18:35:48 Phoenix kernel: [449670.170365] IP: [<f08f9361>] xfs_count_page_state+0x41/0x90 [xfs]
May 15 18:35:48 Phoenix kernel: [449670.170410] *pde = 00000000 
May 15 18:35:48 Phoenix kernel: [449670.170415] Oops: 0000 [#1] SMP 
May 15 18:35:48 Phoenix kernel: [449670.170418] last sysfs file: /sys/devices/virtual/dmi/id/chassis_asset_tag
May 15 18:35:48 Phoenix kernel: [449670.170424] Dumping ftrace buffer:
May 15 18:35:48 Phoenix kernel: [449670.170428]    (ftrace buffer empty)
May 15 18:35:48 Phoenix kernel: [449670.170430] Modules linked in: i915 drm bridge stp bnep input_polldev video output xfs lp ppdev snd_intel8x0 mt2060 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device dvb_usb_dib0700 dib7000p dib7000m dvb_usb dvb_core snd dib3000mc dibx000_common dib0070 pcspkr iTCO_wdt iTCO_vendor_support soundcore snd_page_alloc shpchp parport_pc parport intel_agp agpgart usbhid e100 mii floppy fbcon tileblit font bitblit softcursor
May 15 18:35:48 Phoenix kernel: [449670.170469] 
May 15 18:35:48 Phoenix kernel: [449670.170473] Pid: 24, comm: kswapd0 Not tainted (2.6.28-11-generic #42-Ubuntu) POWERMATE VL4
May 15 18:35:48 Phoenix kernel: [449670.170476] EIP: 0060:[<f08f9361>] EFLAGS: 00010216 CPU: 0
May 15 18:35:48 Phoenix kernel: [449670.170494] EIP is at xfs_count_page_state+0x41/0x90 [xfs]
May 15 18:35:48 Phoenix kernel: [449670.170497] EAX: 19430947 EBX: c14f0840 ECX: df345d80 EDX: b625e08a
May 15 18:35:48 Phoenix kernel: [449670.170500] ESI: ed3add58 EDI: ed3add5c EBP: ed3add14 ESP: ed3add08
May 15 18:35:48 Phoenix kernel: [449670.170503]  DS: 007b ES: 007b FS: 00d8 GS: 0000 SS: 0068
May 15 18:35:48 Phoenix kernel: [449670.170506] Process kswapd0 (pid: 24, ti=ed3ac000 task=eefda5b0 task.ti=ed3ac000)
May 15 18:35:48 Phoenix kernel: [449670.170508] Stack:
May 15 18:35:48 Phoenix kernel: [449670.170510]  c14f0840 000000d0 ed3add54 ed3add6c f08fa4eb ed3add54 00000002 ed3add2c
May 15 18:35:48 Phoenix kernel: [449670.170517]  eeae7500 00000000 00000001 00000000 00000001 00000000 00000000 00000000
May 15 18:35:48 Phoenix kernel: [449670.170523]  00000000 00000000 00000000 00000000 00000001 00000000 c14f0840 000000d0
May 15 18:35:48 Phoenix kernel: [449670.170530] Call Trace:
May 15 18:35:48 Phoenix kernel: [449670.170532]  [<f08fa4eb>] ? xfs_vm_releasepage+0x6b/0xd0 [xfs]
May 15 18:35:48 Phoenix kernel: [449670.170550]  [<c018ef1e>] ? try_to_release_page+0x2e/0x50
May 15 18:35:48 Phoenix kernel: [449670.170562]  [<c019a39d>] ? shrink_page_list+0x41d/0x4e0
May 15 18:35:48 Phoenix kernel: [449670.170569]  [<c019985a>] ? isolate_pages_global+0x5a/0x70
May 15 18:35:48 Phoenix kernel: [449670.170573]  [<c019a601>] ? shrink_inactive_list+0x1a1/0x4d0
May 15 18:35:48 Phoenix kernel: [449670.170578]  [<c019a9d7>] ? shrink_list+0xa7/0xb0
May 15 18:35:48 Phoenix kernel: [449670.170581]  [<c019aa9e>] ? shrink_zone+0xbe/0x1b0
May 15 18:35:48 Phoenix kernel: [449670.170585]  [<c019b4b5>] ? balance_pgdat+0x455/0x470
May 15 18:35:48 Phoenix kernel: [449670.170589]  [<c0199800>] ? isolate_pages_global+0x0/0x70
May 15 18:35:48 Phoenix kernel: [449670.170592]  [<c014ef0a>] ? prepare_to_wait+0x3a/0x70
May 15 18:35:48 Phoenix kernel: [449670.170598]  [<c019b591>] ? kswapd+0xc1/0x110
May 15 18:35:48 Phoenix kernel: [449670.170602]  [<c014ecb0>] ? autoremove_wake_function+0x0/0x50
May 15 18:35:48 Phoenix kernel: [449670.170606]  [<c019b4d0>] ? kswapd+0x0/0x110
May 15 18:35:48 Phoenix kernel: [449670.170609]  [<c014e90c>] ? kthread+0x3c/0x70
May 15 18:35:48 Phoenix kernel: [449670.170612]  [<c014e8d0>] ? kthread+0x0/0x70
May 15 18:35:48 Phoenix kernel: [449670.170615]  [<c0105477>] ? kernel_thread_helper+0x7/0x10
May 15 18:35:48 Phoenix kernel: [449670.170621] Code: 01 00 00 00 00 c7 02 00 00 00 00 8b 03 f6 c4 08 74 52 8b 4b 0c 89 ca eb 12 90 a8 20 75 13 c7 06 01 00 00 00 8b 52 04 39 d1 74 1b <8b> 02 a8 01 75 e9 f6 c4 40 74 1c 8b 45 08 c7 00 01 00 00 00 8b 
May 15 18:35:48 Phoenix kernel: [449670.170656] EIP: [<f08f9361>] xfs_count_page_state+0x41/0x90 [xfs] SS:ESP 0068:ed3add08
May 15 18:35:48 Phoenix kernel: [449670.170689] ---[ end trace a620edaa29282a86 ]---

--------

May 16 07:45:46 Phoenix kernel: [497068.236219] BUG: unable to handle kernel paging request at 00345dc0
May 16 07:45:46 Phoenix kernel: [497068.236231] IP: [<f08f9361>] xfs_count_page_state+0x41/0x90 [xfs]
May 16 07:45:46 Phoenix kernel: [497068.236280] *pde = 00000000 
May 16 07:45:46 Phoenix kernel: [497068.236285] Oops: 0000 [#2] SMP 
May 16 07:45:46 Phoenix kernel: [497068.236288] last sysfs file: /sys/devices/virtual/dmi/id/chassis_asset_tag
May 16 07:45:46 Phoenix kernel: [497068.236293] Modules linked in: i915 drm bridge stp bnep input_polldev video output xfs lp ppdev snd_intel8x0 mt2060 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device dvb_usb_dib0700 dib7000p dib7000m dvb_usb dvb_core snd dib3000mc dibx000_common dib0070 pcspkr iTCO_wdt iTCO_vendor_support soundcore snd_page_alloc shpchp parport_pc parport intel_agp agpgart usbhid e100 mii floppy fbcon tileblit font bitblit softcursor
May 16 07:45:46 Phoenix kernel: [497068.236333] 
May 16 07:45:46 Phoenix kernel: [497068.236337] Pid: 14801, comm: xfs_fsr Tainted: G      D    (2.6.28-11-generic #42-Ubuntu) POWERMATE VL4
May 16 07:45:46 Phoenix kernel: [497068.236340] EIP: 0060:[<f08f9361>] EFLAGS: 00010202 CPU: 0
May 16 07:45:46 Phoenix kernel: [497068.236357] EIP is at xfs_count_page_state+0x41/0x90 [xfs]
May 16 07:45:46 Phoenix kernel: [497068.236360] EAX: 4000080d EBX: c14f0860 ECX: 00345dc0 EDX: 00345dc0
May 16 07:45:46 Phoenix kernel: [497068.236364] ESI: cea03b50 EDI: cea03b54 EBP: cea03b0c ESP: cea03b00
May 16 07:45:46 Phoenix kernel: [497068.236366]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
May 16 07:45:46 Phoenix kernel: [497068.236370] Process xfs_fsr (pid: 14801, ti=cea02000 task=dc1ba5b0 task.ti=cea02000)
May 16 07:45:46 Phoenix kernel: [497068.236372] Stack:
May 16 07:45:46 Phoenix kernel: [497068.236374]  c14f0860 00000000 cea03b4c cea03b64 f08fa4eb cea03b4c c01badb7 cea03b24
May 16 07:45:46 Phoenix kernel: [497068.236381]  eeae7500 00000000 00000001 00000000 00000001 00000000 00000000 00000000
May 16 07:45:46 Phoenix kernel: [497068.236387]  00000000 00000000 00000000 00000000 00000000 00000000 c14f0860 00000000
May 16 07:45:46 Phoenix kernel: [497068.236394] Call Trace:
May 16 07:45:46 Phoenix kernel: [497068.236396]  [<f08fa4eb>] ? xfs_vm_releasepage+0x6b/0xd0 [xfs]
May 16 07:45:46 Phoenix kernel: [497068.236414]  [<c01badb7>] ? __mem_cgroup_uncharge_common+0x137/0x170
May 16 07:45:46 Phoenix kernel: [497068.236426]  [<c018ef1e>] ? try_to_release_page+0x2e/0x50
May 16 07:45:46 Phoenix kernel: [497068.236433]  [<c01987b6>] ? __invalidate_mapping_pages+0x136/0x150
May 16 07:45:46 Phoenix kernel: [497068.236439]  [<c01987e2>] ? invalidate_mapping_pages+0x12/0x20
May 16 07:45:46 Phoenix kernel: [497068.236443]  [<c01d047a>] ? prune_icache+0x21a/0x260
May 16 07:45:46 Phoenix kernel: [497068.236447]  [<c01d04fe>] ? shrink_icache_memory+0x3e/0x50
May 16 07:45:46 Phoenix kernel: [497068.236451]  [<c0198cc7>] ? shrink_slab+0x117/0x170
May 16 07:45:46 Phoenix kernel: [497068.236455]  [<c019adfd>] ? do_try_to_free_pages+0x14d/0x2b0
May 16 07:45:46 Phoenix kernel: [497068.236459]  [<c019b04c>] ? try_to_free_pages+0x6c/0x80
May 16 07:45:46 Phoenix kernel: [497068.236462]  [<c0199800>] ? isolate_pages_global+0x0/0x70
May 16 07:45:46 Phoenix kernel: [497068.236466]  [<c01940b3>] ? __alloc_pages_internal+0x1d3/0x490
May 16 07:45:46 Phoenix kernel: [497068.236470]  [<c0196c32>] ? __do_page_cache_readahead+0xd2/0x1d0
May 16 07:45:46 Phoenix kernel: [497068.236474]  [<c0197019>] ? ondemand_readahead+0xe9/0x140
May 16 07:45:46 Phoenix kernel: [497068.236478]  [<c01970e8>] ? page_cache_async_readahead+0x78/0x90
May 16 07:45:46 Phoenix kernel: [497068.236482]  [<c0190136>] ? do_generic_file_read+0x316/0x4c0
May 16 07:45:46 Phoenix kernel: [497068.236486]  [<c0190383>] ? generic_file_aio_read+0xa3/0x210
May 16 07:45:46 Phoenix kernel: [497068.236489]  [<c018e4b0>] ? file_read_actor+0x0/0xe0
May 16 07:45:46 Phoenix kernel: [497068.236493]  [<f09016b8>] ? xfs_read+0x118/0x280 [xfs]
May 16 07:45:46 Phoenix kernel: [497068.236512]  [<c02cd596>] ? copy_to_user+0x36/0x120
May 16 07:45:46 Phoenix kernel: [497068.236518]  [<f08fd04c>] ? xfs_file_aio_read_invis+0x5c/0x70 [xfs]
May 16 07:45:46 Phoenix kernel: [497068.236537]  [<c01bd531>] ? do_sync_read+0xd1/0x110
May 16 07:45:46 Phoenix kernel: [497068.236542]  [<c014ecb0>] ? autoremove_wake_function+0x0/0x50
May 16 07:45:46 Phoenix kernel: [497068.236549]  [<c02a8ff9>] ? apparmor_file_permission+0x19/0x40
May 16 07:45:46 Phoenix kernel: [497068.236556]  [<c028724f>] ? security_file_permission+0xf/0x20
May 16 07:45:46 Phoenix kernel: [497068.236563]  [<c01bd5c4>] ? rw_verify_area+0x54/0xd0
May 16 07:45:46 Phoenix kernel: [497068.236567]  [<c01bd10d>] ? fsnotify_modify+0x6d/0x80
May 16 07:45:46 Phoenix kernel: [497068.236570]  [<c01bdcb5>] ? vfs_read+0x95/0x100
May 16 07:45:46 Phoenix kernel: [497068.236574]  [<c01bd460>] ? do_sync_read+0x0/0x110
May 16 07:45:46 Phoenix kernel: [497068.236577]  [<c01bdddd>] ? sys_read+0x3d/0x70
May 16 07:45:46 Phoenix kernel: [497068.236580]  [<c0103f6b>] ? sysenter_do_call+0x12/0x2f
May 16 07:45:46 Phoenix kernel: [497068.236585] Code: 01 00 00 00 00 c7 02 00 00 00 00 8b 03 f6 c4 08 74 52 8b 4b 0c 89 ca eb 12 90 a8 20 75 13 c7 06 01 00 00 00 8b 52 04 39 d1 74 1b <8b> 02 a8 01 75 e9 f6 c4 40 74 1c 8b 45 08 c7 00 01 00 00 00 8b 
May 16 07:45:46 Phoenix kernel: [497068.236621] EIP: [<f08f9361>] xfs_count_page_state+0x41/0x90 [xfs] SS:ESP 0068:cea03b00
May 16 07:45:46 Phoenix kernel: [497068.236641] ---[ end trace a620edaa29282a86 ]---

--------

May 17 22:34:07 Phoenix kernel: [45423.473465] BUG: unable to handle kernel paging request at 008add00
May 17 22:34:07 Phoenix kernel: [45423.473479] IP: [<f0919361>] xfs_count_page_state+0x41/0x90 [xfs]
May 17 22:34:07 Phoenix kernel: [45423.473532] *pde = 00000000 
May 17 22:34:07 Phoenix kernel: [45423.473537] Oops: 0000 [#1] SMP 
May 17 22:34:07 Phoenix kernel: [45423.473541] last sysfs file: /sys/devices/pci0000:00/0000:00:1f.1/host0/target0:0:0/0:0:0:0/type
May 17 22:34:08 Phoenix kernel: [45423.473548] Dumping ftrace buffer:
May 17 22:34:08 Phoenix kernel: [45423.473552]    (ftrace buffer empty)
May 17 22:34:08 Phoenix kernel: [45423.473554] Modules linked in: i915 drm bridge stp bnep input_polldev video output xfs lp snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi mt2060 snd_rawmidi ppdev snd_seq_midi_event snd_seq snd_timer snd_seq_device dvb_usb_dib0700 dib7000p dib7000m dvb_usb snd soundcore dvb_core pcspkr snd_page_alloc dib3000mc dibx000_common dib0070 iTCO_wdt iTCO_vendor_support shpchp parport_pc parport intel_agp agpgart usbhid e100 mii floppy fbcon tileblit font bitblit softcursor
May 17 22:34:08 Phoenix kernel: [45423.473594] 
May 17 22:34:08 Phoenix kernel: [45423.473598] Pid: 24, comm: kswapd0 Not tainted (2.6.28-11-generic #42-Ubuntu) POWERMATE VL4
May 17 22:34:08 Phoenix kernel: [45423.473601] EIP: 0060:[<f0919361>] EFLAGS: 00010202 CPU: 0
May 17 22:34:08 Phoenix kernel: [45423.473619] EIP is at xfs_count_page_state+0x41/0x90 [xfs]
May 17 22:34:08 Phoenix kernel: [45423.473622] EAX: 40000809 EBX: c14984c0 ECX: 008add00 EDX: 008add00
May 17 22:34:08 Phoenix kernel: [45423.473625] ESI: ed3add58 EDI: ed3add5c EBP: ed3add14 ESP: ed3add08
May 17 22:34:08 Phoenix kernel: [45423.473627]  DS: 007b ES: 007b FS: 00d8 GS: 0000 SS: 0068
May 17 22:34:08 Phoenix kernel: [45423.473631] Process kswapd0 (pid: 24, ti=ed3ac000 task=eefda5b0 task.ti=ed3ac000)
May 17 22:34:08 Phoenix kernel: [45423.473633] Stack:
May 17 22:34:08 Phoenix kernel: [45423.473634]  c14984c0 000000d0 ed3add54 ed3add6c f091a4eb ed3add54 00000002 ed3add2c
May 17 22:34:08 Phoenix kernel: [45423.473641]  e4243c80 00000000 00000001 00000000 00000001 00000000 00000000 00000000
May 17 22:34:08 Phoenix kernel: [45423.473648]  00000000 00000000 00000000 00000000 00000000 00000000 c14984c0 000000d0
May 17 22:34:08 Phoenix kernel: [45423.473654] Call Trace:
May 17 22:34:08 Phoenix kernel: [45423.473657]  [<f091a4eb>] ? xfs_vm_releasepage+0x6b/0xd0 [xfs]
May 17 22:34:08 Phoenix kernel: [45423.473675]  [<c018ef1e>] ? try_to_release_page+0x2e/0x50
May 17 22:34:08 Phoenix kernel: [45423.473688]  [<c019a39d>] ? shrink_page_list+0x41d/0x4e0
May 17 22:34:08 Phoenix kernel: [45423.473696]  [<c019a601>] ? shrink_inactive_list+0x1a1/0x4d0
May 17 22:34:08 Phoenix kernel: [45423.473700]  [<c019a9d7>] ? shrink_list+0xa7/0xb0
May 17 22:34:08 Phoenix kernel: [45423.473704]  [<c019aa9e>] ? shrink_zone+0xbe/0x1b0
May 17 22:34:08 Phoenix kernel: [45423.473707]  [<c019b4b5>] ? balance_pgdat+0x455/0x470
May 17 22:34:08 Phoenix kernel: [45423.473711]  [<c0199800>] ? isolate_pages_global+0x0/0x70
May 17 22:34:08 Phoenix kernel: [45423.473715]  [<c014ef0a>] ? prepare_to_wait+0x3a/0x70
May 17 22:34:08 Phoenix kernel: [45423.473721]  [<c019b591>] ? kswapd+0xc1/0x110
May 17 22:34:08 Phoenix kernel: [45423.473725]  [<c014ecb0>] ? autoremove_wake_function+0x0/0x50
May 17 22:34:08 Phoenix kernel: [45423.473729]  [<c019b4d0>] ? kswapd+0x0/0x110
May 17 22:34:08 Phoenix kernel: [45423.473732]  [<c014e90c>] ? kthread+0x3c/0x70
May 17 22:34:08 Phoenix kernel: [45423.473735]  [<c014e8d0>] ? kthread+0x0/0x70
May 17 22:34:08 Phoenix kernel: [45423.473738]  [<c0105477>] ? kernel_thread_helper+0x7/0x10
May 17 22:34:08 Phoenix kernel: [45423.473744] Code: 01 00 00 00 00 c7 02 00 00 00 00 8b 03 f6 c4 08 74 52 8b 4b 0c 89 ca eb 12 90 a8 20 75 13 c7 06 01 00 00 00 8b 52 04 39 d1 74 1b <8b> 02 a8 01 75 e9 f6 c4 40 74 1c 8b 45 08 c7 00 01 00 00 00 8b 
May 17 22:34:08 Phoenix kernel: [45423.473780] EIP: [<f0919361>] xfs_count_page_state+0x41/0x90 [xfs] SS:ESP 0068:ed3add08
May 17 22:34:08 Phoenix kernel: [45423.473801] ---[ end trace 9911a01222b80802 ]---

--------

May 18 07:57:32 Phoenix kernel: [79227.793298] BUG: unable to handle kernel paging request at 008add40
May 18 07:57:32 Phoenix kernel: [79227.793309] IP: [<f0919361>] xfs_count_page_state+0x41/0x90 [xfs]
May 18 07:57:32 Phoenix kernel: [79227.793354] *pde = 00000000 
May 18 07:57:32 Phoenix kernel: [79227.793359] Oops: 0000 [#2] SMP 
May 18 07:57:32 Phoenix kernel: [79227.793363] last sysfs file: /sys/devices/pci0000:00/0000:00:1f.1/host0/target0:0:0/0:0:0:0/type
May 18 07:57:32 Phoenix kernel: [79227.793369] Modules linked in: i915 drm bridge stp bnep input_polldev video output xfs lp snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi mt2060 snd_rawmidi ppdev snd_seq_midi_event snd_seq snd_timer snd_seq_device dvb_usb_dib0700 dib7000p dib7000m dvb_usb snd soundcore dvb_core pcspkr snd_page_alloc dib3000mc dibx000_common dib0070 iTCO_wdt iTCO_vendor_support shpchp parport_pc parport intel_agp agpgart usbhid e100 mii floppy fbcon tileblit font bitblit softcursor
May 18 07:57:32 Phoenix kernel: [79227.793409] 
May 18 07:57:32 Phoenix kernel: [79227.793413] Pid: 11878, comm: xfs_fsr Tainted: G      D    (2.6.28-11-generic #42-Ubuntu) POWERMATE VL4
May 18 07:57:32 Phoenix kernel: [79227.793416] EIP: 0060:[<f0919361>] EFLAGS: 00010202 CPU: 0
May 18 07:57:32 Phoenix kernel: [79227.793433] EIP is at xfs_count_page_state+0x41/0x90 [xfs]
May 18 07:57:32 Phoenix kernel: [79227.793436] EAX: 4000080d EBX: c14984e0 ECX: 008add40 EDX: 008add40
May 18 07:57:32 Phoenix kernel: [79227.793439] ESI: e4099b50 EDI: e4099b54 EBP: e4099b0c ESP: e4099b00
May 18 07:57:32 Phoenix kernel: [79227.793442]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
May 18 07:57:32 Phoenix kernel: [79227.793445] Process xfs_fsr (pid: 11878, ti=e4098000 task=d3f357f0 task.ti=e4098000)
May 18 07:57:32 Phoenix kernel: [79227.793447] Stack:
May 18 07:57:32 Phoenix kernel: [79227.793449]  c14984e0 00000000 e4099b4c e4099b64 f091a4eb e4099b4c 00038536 e4099b24
May 18 07:57:32 Phoenix kernel: [79227.793456]  e4243c80 00000000 00000001 00000000 00000001 00000000 00000000 00000000
May 18 07:57:32 Phoenix kernel: [79227.793462]  00000000 00000000 00000000 00000000 00000000 00000000 c14984e0 00000000
May 18 07:57:32 Phoenix kernel: [79227.793469] Call Trace:
May 18 07:57:32 Phoenix kernel: [79227.793471]  [<f091a4eb>] ? xfs_vm_releasepage+0x6b/0xd0 [xfs]
May 18 07:57:32 Phoenix kernel: [79227.793489]  [<c018ef1e>] ? try_to_release_page+0x2e/0x50
May 18 07:57:32 Phoenix kernel: [79227.793500]  [<c01987b6>] ? __invalidate_mapping_pages+0x136/0x150
May 18 07:57:32 Phoenix kernel: [79227.793507]  [<c01987e2>] ? invalidate_mapping_pages+0x12/0x20
May 18 07:57:32 Phoenix kernel: [79227.793511]  [<c01d047a>] ? prune_icache+0x21a/0x260
May 18 07:57:32 Phoenix kernel: [79227.793516]  [<c01d04fe>] ? shrink_icache_memory+0x3e/0x50
May 18 07:57:32 Phoenix kernel: [79227.793519]  [<c0198cc7>] ? shrink_slab+0x117/0x170
May 18 07:57:32 Phoenix kernel: [79227.793523]  [<c019adfd>] ? do_try_to_free_pages+0x14d/0x2b0
May 18 07:57:32 Phoenix kernel: [79227.793527]  [<c019b04c>] ? try_to_free_pages+0x6c/0x80
May 18 07:57:32 Phoenix kernel: [79227.793531]  [<c0199800>] ? isolate_pages_global+0x0/0x70
May 18 07:57:32 Phoenix kernel: [79227.793535]  [<c01940b3>] ? __alloc_pages_internal+0x1d3/0x490
May 18 07:57:32 Phoenix kernel: [79227.793539]  [<c0196c32>] ? __do_page_cache_readahead+0xd2/0x1d0
May 18 07:57:32 Phoenix kernel: [79227.793543]  [<c0197019>] ? ondemand_readahead+0xe9/0x140
May 18 07:57:32 Phoenix kernel: [79227.793547]  [<c01970e8>] ? page_cache_async_readahead+0x78/0x90
May 18 07:57:32 Phoenix kernel: [79227.793551]  [<c0190136>] ? do_generic_file_read+0x316/0x4c0
May 18 07:57:32 Phoenix kernel: [79227.793555]  [<c0190383>] ? generic_file_aio_read+0xa3/0x210
May 18 07:57:32 Phoenix kernel: [79227.793558]  [<c018e4b0>] ? file_read_actor+0x0/0xe0
May 18 07:57:32 Phoenix kernel: [79227.793562]  [<f09216b8>] ? xfs_read+0x118/0x280 [xfs]
May 18 07:57:32 Phoenix kernel: [79227.793580]  [<c02cd596>] ? copy_to_user+0x36/0x120
May 18 07:57:32 Phoenix kernel: [79227.793585]  [<f091d04c>] ? xfs_file_aio_read_invis+0x5c/0x70 [xfs]
May 18 07:57:32 Phoenix kernel: [79227.793604]  [<c01bd531>] ? do_sync_read+0xd1/0x110
May 18 07:57:32 Phoenix kernel: [79227.793609]  [<c014ecb0>] ? autoremove_wake_function+0x0/0x50
May 18 07:57:32 Phoenix kernel: [79227.793616]  [<c02a8ff9>] ? apparmor_file_permission+0x19/0x40
May 18 07:57:32 Phoenix kernel: [79227.793622]  [<c028724f>] ? security_file_permission+0xf/0x20
May 18 07:57:32 Phoenix kernel: [79227.793630]  [<c01bd5c4>] ? rw_verify_area+0x54/0xd0
May 18 07:57:32 Phoenix kernel: [79227.793633]  [<c01bd10d>] ? fsnotify_modify+0x6d/0x80
May 18 07:57:32 Phoenix kernel: [79227.793637]  [<c01bdcb5>] ? vfs_read+0x95/0x100
May 18 07:57:32 Phoenix kernel: [79227.793640]  [<c01bd460>] ? do_sync_read+0x0/0x110
May 18 07:57:32 Phoenix kernel: [79227.793643]  [<c01bdddd>] ? sys_read+0x3d/0x70
May 18 07:57:32 Phoenix kernel: [79227.793647]  [<c0103f6b>] ? sysenter_do_call+0x12/0x2f
May 18 07:57:32 Phoenix kernel: [79227.793651] Code: 01 00 00 00 00 c7 02 00 00 00 00 8b 03 f6 c4 08 74 52 8b 4b 0c 89 ca eb 12 90 a8 20 75 13 c7 06 01 00 00 00 8b 52 04 39 d1 74 1b <8b> 02 a8 01 75 e9 f6 c4 40 74 1c 8b 45 08 c7 00 01 00 00 00 8b 
May 18 07:57:32 Phoenix kernel: [79227.793686] EIP: [<f0919361>] xfs_count_page_state+0x41/0x90 [xfs] SS:ESP 0068:e4099b00
May 18 07:57:32 Phoenix kernel: [79227.793707] ---[ end trace 9911a01222b80802 ]---

[FONT=Tahoma][SIZE=2]Now[/SIZE][/FONT][FONT=Tahoma][SIZE=2], the hardware continues running, but I can no longer connect to SSH (the server is headless), I cannot play any music/videos shared (using samba)[/SIZE][/FONT][FONT=Tahoma][SIZE=2], connecting to my web server (Apache) times out, and MythTV stops recording my programs. The only solution I've been able to use to rectify the situation is to press the reset button, which obviously causes a reboot and then everything is fine... for a few hours.

[/SIZE][/FONT][FONT=Tahoma][SIZE=2]I updated from 8.04/10 (can't remember which) to 9.04 on the 9th/10th of May (using apt-get dist-upgrade) and I do regular apt-get update, apt-get upgrades, so I couldn't tell you if or what may have been installed on the 14/15th which may have kicked this off.[/SIZE][/FONT]

[FONT=Tahoma][SIZE=2]Anyway, if anyone has any ideas, please, feel free to post a reply.

Many thanks.[/SIZE][/FONT]

---

### Post by Vitani on 2009-05-19
I fixed this by telling grub to load kernel 2.6.2_7_-11-generic instead of 2.6.2_8_-11-generic (both are labelled as Ubuntu 9.04). My server's been up for a day and a half now, which is an improvement to say the least.

---

