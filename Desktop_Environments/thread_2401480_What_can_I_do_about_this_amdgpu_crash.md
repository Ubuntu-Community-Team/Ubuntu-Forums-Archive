---
title: "What can I do about this amdgpu crash?"
date: 2018-09-18
forum: Desktop Environments
---

### Post by mntgoat on 2018-09-18
I got a new video card and my machine now hangs after it locks sometimes, like maybe once every couple of days. I'm able to ssh in so I got this out of dmesg. Any ideas of what I can do? I'm on Ubuntu Ubuntu 18.04.1 LTS


```
[162338.011323] ------------[ cut here ]------------
[162338.011325] kernel BUG at /build/linux-SlLHxe/linux-4.15.0/mm/slub.c:296!
[162338.011335] invalid opcode: 0000 [#1] SMP NOPTI
[162338.011337] Modules linked in: nls_iso8859_1 cdc_acm edac_mce_amd kvm_amd kvm snd_hda_codec_realtek irqbypass snd_hda_codec_generic crct10dif_pclmul snd_hda_codec_hdmi crc32_pclmul ghash_clmulni_intel snd_hda_intel snd_hda_codec pcbc snd_hda_core snd_hwdep snd_pcm aesni_intel aes_x86_64 crypto_simd glue_helper joydev cryptd input_leds snd_seq_midi eeepc_wmi snd_seq_midi_event asus_wmi sparse_keymap video snd_rawmidi wmi_bmof snd_seq snd_seq_device snd_timer snd k10temp fam15h_power shpchp soundcore mac_hid sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 amdkfd amd_iommu_v2 hid_generic amdgpu chash firewire_ohci i2c_algo_bit ttm drm_kms_helper firewire_core syscopyarea usbhid sysfillrect crc_itu_t sysimgblt hid fb_sys_fops i2c_piix4 drm ahci r8169 libahci mii wmi
[162338.011396] CPU: 7 PID: 1512 Comm: Xorg Not tainted 4.15.0-34-generic #37-Ubuntu
[162338.011399] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A97 EVO, BIOS 1604 10/16/2012
[162338.011406] RIP: 0010:__slab_free+0x17a/0x2c0
[162338.011408] RSP: 0018:ffffb54e842f39f0 EFLAGS: 00010246
[162338.011412] RAX: ffff90beb6761000 RBX: ffff90beb6761000 RCX: 0000000100200019
[162338.011414] RDX: ffff90beb6761000 RSI: fffff72887d9d800 RDI: ffff90c4de002f00
[162338.011416] RBP: ffffb54e842f3a90 R08: 0000000000000001 R09: ffffffffc0738204
[162338.011418] R10: ffffb54e842f3ab0 R11: 0000000000000000 R12: ffff90c4de002f00
[162338.011421] R13: fffff72887d9d800 R14: ffff90beb6761000 R15: ffff90c130bd1400
[162338.011424] FS:  00007f4c57223600(0000) GS:ffff90c4fedc0000(0000) knlGS:0000000000000000
[162338.011426] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[162338.011428] CR2: 00007f732ff9c070 CR3: 00000008170a6000 CR4: 00000000000406e0
[162338.011430] Call Trace:
[162338.011509]  ? dc_sink_free+0x34/0x40 [amdgpu]
[162338.011513]  kfree+0x165/0x180
[162338.011516]  ? kfree+0x165/0x180
[162338.011563]  dc_sink_free+0x34/0x40 [amdgpu]
[162338.011611]  dc_sink_release+0x24/0x30 [amdgpu]
[162338.011657]  dc_stream_free+0x22/0x50 [amdgpu]
[162338.011704]  dc_stream_release+0x2c/0x30 [amdgpu]
[162338.011752]  amdgpu_dm_connector_mode_valid+0xc9/0x240 [amdgpu]
[162338.011774]  ? drm_mode_connector_list_update+0x113/0x180 [drm]
[162338.011788]  drm_helper_probe_single_connector_modes+0x418/0x710 [drm_kms_helper]
[162338.011802]  drm_mode_getconnector+0x15d/0x340 [drm]
[162338.011806]  ? import_iovec+0x3a/0xe0
[162338.011820]  ? drm_mode_connector_property_set_ioctl+0x60/0x60 [drm]
[162338.011833]  drm_ioctl_kernel+0x5f/0xb0 [drm]
[162338.011845]  drm_ioctl+0x31b/0x3d0 [drm]
[162338.011858]  ? drm_mode_connector_property_set_ioctl+0x60/0x60 [drm]
[162338.011896]  amdgpu_drm_ioctl+0x4f/0x90 [amdgpu]
[162338.011902]  do_vfs_ioctl+0xa8/0x630
[162338.011906]  ? __sys_recvmsg+0x80/0x90
[162338.011910]  SyS_ioctl+0x79/0x90
[162338.011914]  do_syscall_64+0x73/0x130
[162338.011918]  entry_SYSCALL_64_after_hwframe+0x3d/0xa2
[162338.011921] RIP: 0033:0x7f4c545ce5d7
[162338.011923] RSP: 002b:00007ffed12182d8 EFLAGS: 00000246 ORIG_RAX: 0000000000000010
[162338.011926] RAX: ffffffffffffffda RBX: 000055845d21a450 RCX: 00007f4c545ce5d7
[162338.011928] RDX: 00007ffed1218310 RSI: 00000000c05064a7 RDI: 000000000000000c
[162338.011931] RBP: 00007ffed1218310 R08: 0000000000000001 R09: 0000000000000000
[162338.011932] R10: 0000000000000000 R11: 0000000000000246 R12: 00000000c05064a7
[162338.011935] R13: 000000000000000c R14: 000000000000000c R15: 00007ffed1218310
[162338.011937] Code: 0f 84 ee fe ff ff 44 0f b6 7d 8b 80 7d ab 00 79 05 45 84 ff 74 61 48 83 c4 70 5b 41 5a 41 5c 41 5d 41 5e 41 5f 5d 49 8d 62 f8 c3 <0f> 0b 4c 89 d0 4c 89 d7 45 89 fa 48 85 c0 44 0f b6 7d 8b 74 cb 
[162338.011976] RIP: __slab_free+0x17a/0x2c0 RSP: ffffb54e842f39f0
[162338.012014] ---[ end trace 4d79be08ca3f5309 ]---
[162338.020934] [drm] HBR2x4 pass VS=2, PE=0
[162338.021223] [drm] U28E590: [Block 0] 
[162338.021226] [drm] U28E590: [Block 1] 
[162338.021229] [drm] dc_link_detect: manufacturer_id = 2D4C, product_id = C4D, serial_number = 304D534A, manufacture_week = 16, manufacture_year = 28, display_name = U28E590, speaker_flag = 1, audio_mode_count = 1
[162338.021232] [drm] dc_link_detect: mode number = 0, format_code = 1, channel_count = 2, sample_rate = 7, sample_size = 7
[162381.471882] [drm] amdgpu_dm_irq_schedule_work FAILED src 5
[162485.307156] [drm] amdgpu_dm_irq_schedule_work FAILED src 5
[162485.674257] [drm] amdgpu_dm_irq_schedule_work FAILED src 5
[162577.511826] [drm] amdgpu_dm_irq_schedule_work FAILED src 5
[162577.876415] [drm] amdgpu_dm_irq_schedule_work FAILED src 5
[162628.985566] [drm] amdgpu_dm_irq_schedule_work FAILED src 5
[162629.347597] [drm] amdgpu_dm_irq_schedule_work FAILED src 5
[162666.721532] [drm] amdgpu_dm_irq_schedule_work FAILED src 5
[162667.088458] [drm] amdgpu_dm_irq_schedule_work FAILED src 5
[162691.260568] [drm] amdgpu_dm_irq_schedule_work FAILED src 5
[162691.628984] [drm] amdgpu_dm_irq_schedule_work FAILED src 5
[162745.259552] [drm] amdgpu_dm_irq_schedule_work FAILED src 5
[162745.620262] [drm] amdgpu_dm_irq_schedule_work FAILED src 5
[162784.837811] [drm] amdgpu_dm_irq_schedule_work FAILED src 5
[162785.201164] [drm] amdgpu_dm_irq_schedule_work FAILED src 5
[162807.694139] [drm] amdgpu_dm_irq_schedule_work FAILED src 5
[162808.061685] [drm] amdgpu_dm_irq_schedule_work FAILED src 5
[162846.857772] [drm] amdgpu_dm_irq_schedule_work FAILED src 5
[162847.222583] [drm] amdgpu_dm_irq_schedule_work FAILED src 5
[162903.192320] [drm] amdgpu_dm_irq_schedule_work FAILED src 5
[162903.553873] [drm] amdgpu_dm_irq_schedule_work FAILED src 5
[162936.020212] [drm] amdgpu_dm_irq_schedule_work FAILED src 5
[162936.384622] [drm] amdgpu_dm_irq_schedule_work FAILED src 5
[162967.749904] [drm] amdgpu_dm_irq_schedule_work FAILED src 5
[162968.115346] [drm] amdgpu_dm_irq_schedule_work FAILED src 5
[163039.363304] [drm] amdgpu_dm_irq_schedule_work FAILED src 5
[163039.726978] [drm] amdgpu_dm_irq_schedule_work FAILED src 5
[163066.378526] [drm] amdgpu_dm_irq_schedule_work FAILED src 5
[163066.737596] [drm] amdgpu_dm_irq_schedule_work FAILED src 5
[166373.639676] [drm] amdgpu_dm_irq_schedule_work FAILED src 5
[166374.053124] [drm] amdgpu_dm_irq_schedule_work FAILED src 5

```

---

### Post by leblutch on 2018-10-17
Hi,

getting the exact same BUG and same behavior..

anyone has a workaround / pointer ?

Thx..

---

### Post by mntgoat on 2018-10-17
> **leblutch said:**
> Hi,

getting the exact same BUG and same behavior..

anyone has a workaround / pointer ?

Thx..

My video card was just a couple of weeks old so I returned it and got a different one, issues went away.

---

