---
title: "Asus G14 and two ext. displays [again]"
date: 2021-07-22
forum: Desktop Environments
---

### Post by dbehterev on 2021-07-22
Hello community, I again have question with my laptop asus G14 and two external displays. I already placed my question [https://ubuntuforums.org/showthread.php?t=2455965](https://ubuntuforums.org/showthread.php?t=2455965) but since that moment nothing has changed. I spent ton of time without success.
I have installed Ubuntu 20.04.1 LTS alongside with my Windows 10 installation.
Nvidia 460 driver recognised my ext. display that is connected to NVidia GPU but this display didn't work (it always switched off). Only ext. display that is connected to the AMD GPU is working.
After many hours trying to understand where is problem I decided to give up this path. Moreover, only kernel 5.7.0 seems to work because any other higher version of kernel cause another problems with my installation: after some period of time (approx. 5 min) my external Dell Thunderbolt adapter stops working and Network hangs (I use built-in LAN port in this adapter). Some kernel versions cause artefacts on built-in display - I see a lot of random lines and dots on display.
Today I booted from Ubuntu 20.04.2 LTS USB flash and voila all two ext. displays work as expected! As I understood everything is working on xorg server on noveau driver that comes with Ubuntu distrib. 
So my question - is it possible somehow transfer Xorg configuration correctly on my installation? I tried deinstall nvidia 460 driver but it doesn't help. Another option that installer suggested is full reinstallation but this way is not good for me but possible.

---

### Post by dbehterev on 2021-07-25
Eventually I reinstalled Ubuntu on 20.04.2 LTS. Because on previous version I had many problems that I couldn't cope. I chose built-in nouveau driver so all my two ext. displays work as expected. But..after some time the second external display that was connected to the NVidia GPU stopped working. Some logs from syslog:

```
Jul 25 11:17:35 bds-linux kernel: [ 2416.880087] [drm] Failed to add display topology, DTM TA is not initialized.
Jul 25 09:32:47 bds-linux kernel: [ 2362.361763] nouveau 0000:01:00.0: timeout
Jul 25 09:32:47 bds-linux kernel: [ 2362.361794] WARNING: CPU: 2 PID: 2552 at drivers/gpu/drm/nouveau/nvkm/subdev/bar/g84.c:35 g84_bar_flush+0xd6/0xe0 [nouveau]
Jul 25 09:32:47 bds-linux kernel: [ 2362.361794] Modules linked in: dm_crypt binfmt_misc rfcomm cmac algif_hash algif_skcipher af_alg bnep snd_hda_codec_realtek snd_hda_codec_generic ledtrig_audio edac_mce_amd snd_hda_codec_hdmi kvm_amd iwlmvm kvm snd_hda_intel crct10dif_pclmul mac80211 snd_intel_dspcfg ghash_clmulni_intel snd_hda_codec aesni_intel snd_hda_core snd_hwdep nls_iso8859_1 crypto_simd snd_pcm amdgpu nouveau libarc4 cryptd snd_seq_midi glue_helper snd_seq_midi_event rapl snd_rawmidi iommu_v2 snd_seq gpu_sched btusb mxm_wmi ttm btrtl btbcm snd_seq_device iwlwifi btintel snd_timer drm_kms_helper apple_mfi_fastcharge bluetooth cdc_ether cec usbnet rc_core r8152 joydev snd_rn_pci_acp3x i2c_algo_bit snd mii efi_pstore ecdh_generic fb_sys_fops input_leds ecc hid_multitouch k10temp cfg80211 snd_pci_acp3x syscopyarea sysfillrect wmi_bmof sysimgblt ccp soundcore asus_nb_wmi ucsi_ccg ucsi_acpi typec_ucsi typec asus_wireless mac_hid sch_fq_codel parport_pc ppdev lp parport drm ip_tables x_tables autofs4 hid_apple usbhid
Jul 25 09:32:47 bds-linux kernel: [ 2362.361812]  hid_generic asus_wmi sparse_keymap mfd_aaeon crc32_pclmul nvme ahci i2c_piix4 libahci nvme_core xhci_pci i2c_nvidia_gpu xhci_pci_renesas wmi video i2c_hid hid
Jul 25 09:32:47 bds-linux kernel: [ 2362.361816] CPU: 2 PID: 2552 Comm: Xorg Tainted: G        W         5.8.0-63-generic #71~20.04.1-Ubuntu
Jul 25 09:32:47 bds-linux kernel: [ 2362.361817] Hardware name: ASUSTeK COMPUTER INC. ROG Zephyrus G14 GA401IV_GA401IV/GA401IV, BIOS GA401IV.219 12/30/2020
Jul 25 09:32:47 bds-linux kernel: [ 2362.361835] RIP: 0010:g84_bar_flush+0xd6/0xe0 [nouveau]
Jul 25 09:32:47 bds-linux kernel: [ 2362.361836] Code: 8b 40 10 48 8b 78 10 4c 8b 77 50 4d 85 f6 75 03 4c 8b 37 e8 cc d1 b5 ea 4c 89 f2 48 c7 c7 ac e5 d5 c0 48 89 c6 e8 92 bf f2 ea <0f> 0b eb a6 e8 11 3d f8 ea 90 0f 1f 44 00 00 55 49 89 d0 b9 00 02
Jul 25 09:32:47 bds-linux kernel: [ 2362.361836] RSP: 0018:ffffaac34400bad8 EFLAGS: 00010086
Jul 25 09:32:47 bds-linux kernel: [ 2362.361837] RAX: 0000000000000000 RBX: ffff8a1e54d68c00 RCX: 0000000000000027
Jul 25 09:32:47 bds-linux kernel: [ 2362.361837] RDX: 0000000000000027 RSI: 0000000000000086 RDI: ffff8a1e5f698cd8
Jul 25 09:32:47 bds-linux kernel: [ 2362.361838] RBP: ffffaac34400bb28 R08: ffff8a1e5f698cd0 R09: 0000000000000004
Jul 25 09:32:47 bds-linux kernel: [ 2362.361838] R10: 0000000000000000 R11: 0000000000000001 R12: ffff8a1e533ac6c8
Jul 25 09:32:47 bds-linux kernel: [ 2362.361838] R13: 0000000000000246 R14: ffff8a1e5cb44890 R15: 0000022603f8ff95
Jul 25 09:32:47 bds-linux kernel: [ 2362.361839] FS:  00007fa048c54a40(0000) GS:ffff8a1e5f680000(0000) knlGS:0000000000000000
Jul 25 09:32:47 bds-linux kernel: [ 2362.361839] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Jul 25 09:32:47 bds-linux kernel: [ 2362.361840] CR2: 00007f22ac01e188 CR3: 00000003bbeb4000 CR4: 0000000000340ee0
Jul 25 09:32:47 bds-linux kernel: [ 2362.361840] Call Trace:
Jul 25 09:32:47 bds-linux kernel: [ 2362.361858]  nvkm_bar_flush+0x1f/0x30 [nouveau]
Jul 25 09:32:47 bds-linux kernel: [ 2362.361879]  nv50_instobj_release+0x2e/0xa0 [nouveau]
Jul 25 09:32:47 bds-linux kernel: [ 2362.361900]  nvkm_instobj_load+0x54/0xb0 [nouveau]
Jul 25 09:32:47 bds-linux kernel: [ 2362.361920]  nvkm_instmem_init+0x68/0x80 [nouveau]
Jul 25 09:32:47 bds-linux kernel: [ 2362.361939]  nvkm_subdev_init+0x99/0xd0 [nouveau]
Jul 25 09:32:47 bds-linux kernel: [ 2362.361940]  ? ktime_get+0x3e/0xa0
Jul 25 09:32:47 bds-linux kernel: [ 2362.361964]  nvkm_device_init+0x118/0x1a0 [nouveau]
Jul 25 09:32:47 bds-linux kernel: [ 2362.361989]  nvkm_udevice_init+0x48/0x60 [nouveau]
Jul 25 09:32:47 bds-linux kernel: [ 2362.362006]  nvkm_object_init+0x43/0x110 [nouveau]
Jul 25 09:32:47 bds-linux kernel: [ 2362.362021]  nvkm_object_init+0x74/0x110 [nouveau]
Jul 25 09:32:47 bds-linux kernel: [ 2362.362037]  nvkm_object_init+0x74/0x110 [nouveau]
Jul 25 09:32:47 bds-linux kernel: [ 2362.362057]  nvkm_client_resume+0xe/0x10 [nouveau]
Jul 25 09:32:47 bds-linux kernel: [ 2362.362072]  nvif_client_resume+0x1d/0x20 [nouveau]
Jul 25 09:32:47 bds-linux kernel: [ 2362.362089]  nouveau_do_resume+0x2e/0xc0 [nouveau]
Jul 25 09:32:47 bds-linux kernel: [ 2362.362106]  nouveau_pmops_runtime_resume+0x86/0x160 [nouveau]
Jul 25 09:32:47 bds-linux kernel: [ 2362.362109]  pci_pm_runtime_resume+0x74/0x90
Jul 25 09:32:47 bds-linux kernel: [ 2362.362111]  ? pci_pm_default_resume+0x30/0x30
Jul 25 09:32:47 bds-linux kernel: [ 2362.362113]  __rpm_callback+0xd0/0x150
Jul 25 09:32:47 bds-linux kernel: [ 2362.362115]  ? pci_pm_default_resume+0x30/0x30
Jul 25 09:32:47 bds-linux kernel: [ 2362.362116]  rpm_callback+0x24/0x80
Jul 25 09:32:47 bds-linux kernel: [ 2362.362117]  ? pci_pm_default_resume+0x30/0x30
Jul 25 09:32:47 bds-linux kernel: [ 2362.362118]  rpm_resume+0x56e/0x780
Jul 25 09:32:47 bds-linux kernel: [ 2362.362120]  ? ktime_get+0x3e/0xa0
Jul 25 09:32:47 bds-linux kernel: [ 2362.362121]  __pm_runtime_resume+0x52/0x80
Jul 25 09:32:47 bds-linux kernel: [ 2362.362138]  nouveau_drm_ioctl+0x40/0xc0 [nouveau]
Jul 25 09:32:47 bds-linux kernel: [ 2362.362141]  ksys_ioctl+0x9d/0xd0
Jul 25 09:32:47 bds-linux kernel: [ 2362.362142]  __x64_sys_ioctl+0x1a/0x20
Jul 25 09:32:47 bds-linux kernel: [ 2362.362145]  do_syscall_64+0x49/0xc0
Jul 25 09:32:47 bds-linux kernel: [ 2362.362148]  entry_SYSCALL_64_after_hwframe+0x44/0xa9
Jul 25 09:32:47 bds-linux kernel: [ 2362.362149] RIP: 0033:0x7fa048fb450b
Jul 25 09:32:47 bds-linux kernel: [ 2362.362151] Code: 0f 1e fa 48 8b 05 85 39 0d 00 64 c7 00 26 00 00 00 48 c7 c0 ff ff ff ff c3 66 0f 1f 44 00 00 f3 0f 1e fa b8 10 00 00 00 0f 05 <48> 3d 01 f0 ff ff 73 01 c3 48 8b 0d 55 39 0d 00 f7 d8 64 89 01 48
Jul 25 09:32:47 bds-linux kernel: [ 2362.362152] RSP: 002b:00007ffd0e955118 EFLAGS: 00000246 ORIG_RAX: 0000000000000010
Jul 25 09:32:47 bds-linux kernel: [ 2362.362154] RAX: ffffffffffffffda RBX: 00007ffd0e955160 RCX: 00007fa048fb450b
Jul 25 09:32:47 bds-linux kernel: [ 2362.362155] RDX: 00007ffd0e955160 RSI: 00000000c05064a7 RDI: 000000000000000c
Jul 25 09:32:47 bds-linux kernel: [ 2362.362156] RBP: 00000000c05064a7 R08: 0000000000000007 R09: 0000000000000008
Jul 25 09:32:47 bds-linux kernel: [ 2362.362157] R10: 0000000000000000 R11: 0000000000000246 R12: 0000000000000001
Jul 25 09:32:47 bds-linux kernel: [ 2362.362157] R13: 000000000000000c R14: 00007ffd0e955160 R15: 00005579e638c480
Jul 25 09:32:47 bds-linux kernel: [ 2362.362158] ---[ end trace 61663f3b59e4a98d ]---
Jul 25 09:32:47 bds-linux kernel: [ 2362.362182] nouveau 0000:01:00.0: tmr: stalled at ffffffffffffffff

```
and another:
```

Jul 25 09:32:47 bds-linux kernel: [ 2362.365379] nouveau 0000:01:00.0: fb: Falcon mem scrubbing timeout
Jul 25 09:32:47 bds-linux kernel: [ 2362.365382] nouveau 0000:01:00.0: fb: VPR still locked after scrub!
Jul 25 09:32:47 bds-linux kernel: [ 2362.365382] nouveau 0000:01:00.0: fb: init failed, -5
Jul 25 09:32:47 bds-linux kernel: [ 2362.365529] nouveau 0000:01:00.0: init failed with -5
Jul 25 09:32:47 bds-linux kernel: [ 2362.365531] nouveau: systemd-logind[1417]:00000000:00000080: init failed with -5
Jul 25 09:32:47 bds-linux kernel: [ 2362.365532] nouveau: DRM-master:00000000:00000000: init failed with -5
Jul 25 09:32:47 bds-linux kernel: [ 2362.365533] nouveau: DRM-master:00000000:00000000: init failed with -5
Jul 25 09:32:47 bds-linux kernel: [ 2362.365535] nouveau 0000:01:00.0: DRM: Client resume failed with error: -5
Jul 25 09:32:47 bds-linux kernel: [ 2362.365535] nouveau 0000:01:00.0: DRM: resume failed with: -5
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): EDID vendor "NCP", prod id 80
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Using hsync ranges from config file
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Using vrefresh ranges from config file
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Printing DDC gathered Modelines:
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Modeline "1920x1080"x0.0  335.38  1920 1968 2000 2180  1080 1083 1088 1282 +hsync -vsync (153.8 kHz eP)
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Modeline "1920x1080"x0.0  167.69  1920 1968 2000 2180  1080 1083 1088 1282 +hsync -vsync (76.9 kHz e)
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (--) AMDGPU(0): HDMI max TMDS frequency 300000KHz
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): EDID vendor "NCP", prod id 80
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Using hsync ranges from config file
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Using vrefresh ranges from config file
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Printing DDC gathered Modelines:
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Modeline "1920x1080"x0.0  335.38  1920 1968 2000 2180  1080 1083 1088 1282 +hsync -vsync (153.8 kHz eP)
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Modeline "1920x1080"x0.0  167.69  1920 1968 2000 2180  1080 1083 1088 1282 +hsync -vsync (76.9 kHz e)
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (--) AMDGPU(0): HDMI max TMDS frequency 300000KHz
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): EDID vendor "NCP", prod id 80
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Using hsync ranges from config file
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Using vrefresh ranges from config file
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Printing DDC gathered Modelines:
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Modeline "1920x1080"x0.0  335.38  1920 1968 2000 2180  1080 1083 1088 1282 +hsync -vsync (153.8 kHz eP)
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Modeline "1920x1080"x0.0  167.69  1920 1968 2000 2180  1080 1083 1088 1282 +hsync -vsync (76.9 kHz e)
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (--) AMDGPU(0): HDMI max TMDS frequency 300000KHz
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: nouveau: kernel rejected pushbuf: Invalid argument
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: nouveau: ch3: krec 0 pushes 1 bufs 8 relocs 0
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: nouveau: ch3: buf 00000000 00000004 00000004 00000004 00000000
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: nouveau: ch3: buf 00000001 00000008 00000002 00000002 00000002
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: nouveau: ch3: buf 00000002 0000000a 00000002 00000002 00000000
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: nouveau: ch3: buf 00000003 00000006 00000004 00000000 00000004
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: nouveau: ch3: buf 00000004 00000012 00000002 00000000 00000002
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: nouveau: ch3: buf 00000005 00000011 00000004 00000004 00000000
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: nouveau: ch3: buf 00000006 00000007 00000002 00000002 00000000
Jul 25 09:32:47 bds-linux rtkit-daemon[1653]: Supervising 3 threads of 1 processes of 1 users.
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: nouveau: ch3: buf 00000007 0000000b 00000004 00000004 00000000
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: nouveau: ch3: psh 00000000 0000068988 0000068a24
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: nouveau: #0110x20020381
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: nouveau: #0110x0780077c
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: nouveau: #0110x042f0417
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: nouveau: #0110x200308e0
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: nouveau: #0110x00010000
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: nouveau: #0110x00000000
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: nouveau: #0110x007a0000
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: nouveau: #0110xa00d08e3
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: nouveau: #0110x00000000
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: message repeated 4 times: [ nouveau: #0110x00000000]
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: nouveau: #0110x3a088889
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: nouveau: #0110x3a72b9d6
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: nouveau: #0110x00000000
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: nouveau: #0110x00000000
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: nouveau: #0110x3a888889
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: nouveau: #0110xbf800000
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: nouveau: #0110x3af2b9d6
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: nouveau: #0110xbf800000
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: nouveau: #0110x20030700
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: nouveau: #0110x00001004
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: nouveau: #0110x00000000
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: nouveau: #0110x048e0b28
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: nouveau: #0110x20020180
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: nouveau: #0110x00000000
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: nouveau: #0110x048fffff
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: nouveau: #0110x20010586
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: nouveau: #0110x00000006
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: nouveau: #0110x2002035d
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: nouveau: #0110x00000000
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: nouveau: #0110x00000004
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: nouveau: #0110x80000585
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: nouveau: #0110x200406c0
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: nouveau: #0110x00000000
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: nouveau: #0110x00014000
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: nouveau: #0110x000060b6
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: nouveau: #0110x1000f010
Jul 25 09:32:47 bds-linux rtkit-daemon[1653]: Successfully made thread 24601 of process 2461 owned by '1000' RT at priority 5.
Jul 25 09:32:47 bds-linux rtkit-daemon[1653]: Supervising 4 threads of 1 processes of 1 users.
Jul 25 09:32:47 bds-linux kernel: [ 2362.391302] [drm] Failed to add display topology, DTM TA is not initialized.
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Allocate new frame buffer 4480x1440
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0):  => pitch 17920 bytes
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): EDID vendor "NCP", prod id 80
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Using hsync ranges from config file
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Using vrefresh ranges from config file
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Printing DDC gathered Modelines:
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Modeline "1920x1080"x0.0  335.38  1920 1968 2000 2180  1080 1083 1088 1282 +hsync -vsync (153.8 kHz eP)
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Modeline "1920x1080"x0.0  167.69  1920 1968 2000 2180  1080 1083 1088 1282 +hsync -vsync (76.9 kHz e)
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (--) AMDGPU(0): HDMI max TMDS frequency 300000KHz
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): EDID vendor "NCP", prod id 80
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Using hsync ranges from config file
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Using vrefresh ranges from config file
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Printing DDC gathered Modelines:
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Modeline "1920x1080"x0.0  335.38  1920 1968 2000 2180  1080 1083 1088 1282 +hsync -vsync (153.8 kHz eP)
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Modeline "1920x1080"x0.0  167.69  1920 1968 2000 2180  1080 1083 1088 1282 +hsync -vsync (76.9 kHz e)
Jul 25 09:32:47 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (--) AMDGPU(0): HDMI max TMDS frequency 300000KHz
Jul 25 09:32:53 bds-linux systemd[1]: Started Run anacron jobs.
Jul 25 09:32:53 bds-linux anacron[24633]: Anacron 2.3 started on 2021-07-25
Jul 25 09:32:53 bds-linux anacron[24633]: Normal exit (0 jobs run)
Jul 25 09:32:53 bds-linux systemd[1]: anacron.service: Succeeded.
Jul 25 09:32:59 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): EDID vendor "NCP", prod id 80
Jul 25 09:32:59 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Using hsync ranges from config file
Jul 25 09:32:59 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Using vrefresh ranges from config file
Jul 25 09:32:59 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Printing DDC gathered Modelines:
Jul 25 09:32:59 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Modeline "1920x1080"x0.0  335.38  1920 1968 2000 2180  1080 1083 1088 1282 +hsync -vsync (153.8 kHz eP)
Jul 25 09:32:59 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Modeline "1920x1080"x0.0  167.69  1920 1968 2000 2180  1080 1083 1088 1282 +hsync -vsync (76.9 kHz e)
Jul 25 09:32:59 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): EDID vendor "NCP", prod id 80
Jul 25 09:32:59 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Using hsync ranges from config file
Jul 25 09:32:59 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Using vrefresh ranges from config file
Jul 25 09:32:59 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Printing DDC gathered Modelines:
Jul 25 09:32:59 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Modeline "1920x1080"x0.0  335.38  1920 1968 2000 2180  1080 1083 1088 1282 +hsync -vsync (153.8 kHz eP)
Jul 25 09:32:59 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Modeline "1920x1080"x0.0  167.69  1920 1968 2000 2180  1080 1083 1088 1282 +hsync -vsync (76.9 kHz e)
Jul 25 09:32:59 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): EDID vendor "NCP", prod id 80
Jul 25 09:32:59 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Using hsync ranges from config file
Jul 25 09:32:59 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Using vrefresh ranges from config file
Jul 25 09:32:59 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Printing DDC gathered Modelines:
Jul 25 09:32:59 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Modeline "1920x1080"x0.0  335.38  1920 1968 2000 2180  1080 1083 1088 1282 +hsync -vsync (153.8 kHz eP)
Jul 25 09:32:59 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Modeline "1920x1080"x0.0  167.69  1920 1968 2000 2180  1080 1083 1088 1282 +hsync -vsync (76.9 kHz e)
Jul 25 09:32:59 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (EE) AMDGPU(0): drmmode_do_crtc_dpms cannot get last vblank counter
Jul 25 09:33:00 bds-linux kernel: [ 2362.513732] [drm] Failed to add display topology, DTM TA is not initialized.
Jul 25 09:32:59 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (EE) AMDGPU(0): drmmode_do_crtc_dpms cannot get last vblank counter
Jul 25 09:33:00 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Allocate new frame buffer 1920x1080
Jul 25 09:33:00 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0):  => pitch 7680 bytes
Jul 25 09:33:00 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): EDID vendor "NCP", prod id 80
Jul 25 09:33:00 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Using hsync ranges from config file
Jul 25 09:33:00 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Using vrefresh ranges from config file
Jul 25 09:33:00 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Printing DDC gathered Modelines:
Jul 25 09:33:00 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Modeline "1920x1080"x0.0  335.38  1920 1968 2000 2180  1080 1083 1088 1282 +hsync -vsync (153.8 kHz eP)
Jul 25 09:33:00 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Modeline "1920x1080"x0.0  167.69  1920 1968 2000 2180  1080 1083 1088 1282 +hsync -vsync (76.9 kHz e)
Jul 25 09:33:00 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): EDID vendor "NCP", prod id 80
Jul 25 09:33:00 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Using hsync ranges from config file
Jul 25 09:33:00 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Using vrefresh ranges from config file
Jul 25 09:33:00 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Printing DDC gathered Modelines:
Jul 25 09:33:00 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Modeline "1920x1080"x0.0  335.38  1920 1968 2000 2180  1080 1083 1088 1282 +hsync -vsync (153.8 kHz eP)
Jul 25 09:33:00 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Modeline "1920x1080"x0.0  167.69  1920 1968 2000 2180  1080 1083 1088 1282 +hsync -vsync (76.9 kHz e)
Jul 25 09:33:01 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): EDID vendor "NCP", prod id 80
Jul 25 09:33:01 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Using hsync ranges from config file
Jul 25 09:33:01 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Using vrefresh ranges from config file
Jul 25 09:33:01 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Printing DDC gathered Modelines:
Jul 25 09:33:01 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Modeline "1920x1080"x0.0  335.38  1920 1968 2000 2180  1080 1083 1088 1282 +hsync -vsync (153.8 kHz eP)
Jul 25 09:33:01 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Modeline "1920x1080"x0.0  167.69  1920 1968 2000 2180  1080 1083 1088 1282 +hsync -vsync (76.9 kHz e)
Jul 25 09:33:01 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (--) AMDGPU(0): HDMI max TMDS frequency 300000KHz
Jul 25 09:33:01 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Allocate new frame buffer 4480x1440
Jul 25 09:33:01 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0):  => pitch 17920 bytes
Jul 25 09:33:01 bds-linux kernel: [ 2375.223769] [drm] Failed to add display topology, DTM TA is not initialized.
Jul 25 09:33:01 bds-linux rtkit-daemon[1653]: Supervising 3 threads of 1 processes of 1 users.
Jul 25 09:33:01 bds-linux rtkit-daemon[1653]: Successfully made thread 24695 of process 2461 owned by '1000' RT at priority 5.
Jul 25 09:33:01 bds-linux rtkit-daemon[1653]: Supervising 4 threads of 1 processes of 1 users.
Jul 25 09:33:01 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): EDID vendor "NCP", prod id 80
Jul 25 09:33:01 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Using hsync ranges from config file
Jul 25 09:33:01 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Using vrefresh ranges from config file
Jul 25 09:33:01 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Printing DDC gathered Modelines:
Jul 25 09:33:01 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Modeline "1920x1080"x0.0  335.38  1920 1968 2000 2180  1080 1083 1088 1282 +hsync -vsync (153.8 kHz eP)
Jul 25 09:33:01 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Modeline "1920x1080"x0.0  167.69  1920 1968 2000 2180  1080 1083 1088 1282 +hsync -vsync (76.9 kHz e)
Jul 25 09:33:01 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (--) AMDGPU(0): HDMI max TMDS frequency 300000KHz
Jul 25 09:33:01 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): EDID vendor "NCP", prod id 80
Jul 25 09:33:01 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Using hsync ranges from config file
Jul 25 09:33:01 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Using vrefresh ranges from config file
Jul 25 09:33:01 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Printing DDC gathered Modelines:
Jul 25 09:33:01 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Modeline "1920x1080"x0.0  335.38  1920 1968 2000 2180  1080 1083 1088 1282 +hsync -vsync (153.8 kHz eP)
Jul 25 09:33:01 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Modeline "1920x1080"x0.0  167.69  1920 1968 2000 2180  1080 1083 1088 1282 +hsync -vsync (76.9 kHz e)
Jul 25 09:33:01 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (--) AMDGPU(0): HDMI max TMDS frequency 300000KHz
Jul 25 09:33:01 bds-linux colord[1470]: failed to get session [pid 2939]: No data available
Jul 25 09:33:40 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): EDID vendor "NCP", prod id 80
Jul 25 09:33:40 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Using hsync ranges from config file
Jul 25 09:33:40 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Using vrefresh ranges from config file
Jul 25 09:33:40 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Printing DDC gathered Modelines:
Jul 25 09:33:40 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Modeline "1920x1080"x0.0  335.38  1920 1968 2000 2180  1080 1083 1088 1282 +hsync -vsync (153.8 kHz eP)
Jul 25 09:33:40 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Modeline "1920x1080"x0.0  167.69  1920 1968 2000 2180  1080 1083 1088 1282 +hsync -vsync (76.9 kHz e)
Jul 25 09:33:40 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): EDID vendor "NCP", prod id 80
Jul 25 09:33:40 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Using hsync ranges from config file
Jul 25 09:33:40 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Using vrefresh ranges from config file
Jul 25 09:33:40 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Printing DDC gathered Modelines:
Jul 25 09:33:40 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Modeline "1920x1080"x0.0  335.38  1920 1968 2000 2180  1080 1083 1088 1282 +hsync -vsync (153.8 kHz eP)
Jul 25 09:33:40 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Modeline "1920x1080"x0.0  167.69  1920 1968 2000 2180  1080 1083 1088 1282 +hsync -vsync (76.9 kHz e)
Jul 25 09:33:40 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): EDID vendor "NCP", prod id 80
Jul 25 09:33:40 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Using hsync ranges from config file
Jul 25 09:33:40 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Using vrefresh ranges from config file
Jul 25 09:33:40 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Printing DDC gathered Modelines:
Jul 25 09:33:40 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Modeline "1920x1080"x0.0  335.38  1920 1968 2000 2180  1080 1083 1088 1282 +hsync -vsync (153.8 kHz eP)
Jul 25 09:33:40 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Modeline "1920x1080"x0.0  167.69  1920 1968 2000 2180  1080 1083 1088 1282 +hsync -vsync (76.9 kHz e)
Jul 25 09:33:40 bds-linux kernel: [ 2376.799678] [drm] Failed to add display topology, DTM TA is not initialized.
Jul 25 09:33:40 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Allocate new frame buffer 1920x1080
Jul 25 09:33:40 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0):  => pitch 7680 bytes
Jul 25 09:33:40 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): EDID vendor "NCP", prod id 80
Jul 25 09:33:40 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Using hsync ranges from config file
Jul 25 09:33:40 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Using vrefresh ranges from config file
Jul 25 09:33:40 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Printing DDC gathered Modelines:
Jul 25 09:33:40 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Modeline "1920x1080"x0.0  335.38  1920 1968 2000 2180  1080 1083 1088 1282 +hsync -vsync (153.8 kHz eP)
Jul 25 09:33:40 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Modeline "1920x1080"x0.0  167.69  1920 1968 2000 2180  1080 1083 1088 1282 +hsync -vsync (76.9 kHz e)
Jul 25 09:33:40 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): EDID vendor "NCP", prod id 80
Jul 25 09:33:40 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Using hsync ranges from config file
Jul 25 09:33:40 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Using vrefresh ranges from config file
Jul 25 09:33:40 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Printing DDC gathered Modelines:
Jul 25 09:33:40 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Modeline "1920x1080"x0.0  335.38  1920 1968 2000 2180  1080 1083 1088 1282 +hsync -vsync (153.8 kHz eP)
Jul 25 09:33:40 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Modeline "1920x1080"x0.0  167.69  1920 1968 2000 2180  1080 1083 1088 1282 +hsync -vsync (76.9 kHz e)
Jul 25 09:33:41 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): EDID vendor "NCP", prod id 80
Jul 25 09:33:41 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Using hsync ranges from config file
Jul 25 09:33:41 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Using vrefresh ranges from config file
Jul 25 09:33:41 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Printing DDC gathered Modelines:
Jul 25 09:33:41 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Modeline "1920x1080"x0.0  335.38  1920 1968 2000 2180  1080 1083 1088 1282 +hsync -vsync (153.8 kHz eP)
Jul 25 09:33:41 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Modeline "1920x1080"x0.0  167.69  1920 1968 2000 2180  1080 1083 1088 1282 +hsync -vsync (76.9 kHz e)
Jul 25 09:33:41 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (--) AMDGPU(0): HDMI max TMDS frequency 300000KHz
Jul 25 09:33:41 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Allocate new frame buffer 4480x1440
Jul 25 09:33:41 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0):  => pitch 17920 bytes
Jul 25 09:33:41 bds-linux kernel: [ 2415.591601] [drm] Failed to add display topology, DTM TA is not initialized.
Jul 25 09:33:41 bds-linux rtkit-daemon[1653]: Supervising 3 threads of 1 processes of 1 users.
Jul 25 09:33:41 bds-linux rtkit-daemon[1653]: Successfully made thread 24771 of process 2461 owned by '1000' RT at priority 5.
Jul 25 09:33:41 bds-linux rtkit-daemon[1653]: Supervising 4 threads of 1 processes of 1 users.
Jul 25 09:33:41 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): EDID vendor "NCP", prod id 80
Jul 25 09:33:41 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Using hsync ranges from config file
Jul 25 09:33:41 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Using vrefresh ranges from config file
Jul 25 09:33:41 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Printing DDC gathered Modelines:
Jul 25 09:33:41 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Modeline "1920x1080"x0.0  335.38  1920 1968 2000 2180  1080 1083 1088 1282 +hsync -vsync (153.8 kHz eP)
Jul 25 09:33:41 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Modeline "1920x1080"x0.0  167.69  1920 1968 2000 2180  1080 1083 1088 1282 +hsync -vsync (76.9 kHz e)
Jul 25 09:33:41 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (--) AMDGPU(0): HDMI max TMDS frequency 300000KHz
Jul 25 09:33:41 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): EDID vendor "NCP", prod id 80
Jul 25 09:33:41 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Using hsync ranges from config file
Jul 25 09:33:41 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Using vrefresh ranges from config file
Jul 25 09:33:41 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Printing DDC gathered Modelines:
Jul 25 09:33:41 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Modeline "1920x1080"x0.0  335.38  1920 1968 2000 2180  1080 1083 1088 1282 +hsync -vsync (153.8 kHz eP)
Jul 25 09:33:41 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (II) AMDGPU(0): Modeline "1920x1080"x0.0  167.69  1920 1968 2000 2180  1080 1083 1088 1282 +hsync -vsync (76.9 kHz e)
Jul 25 09:33:41 bds-linux /usr/lib/gdm3/gdm-x-session[2552]: (--) AMDGPU(0): HDMI max TMDS frequency 300000KHz

```

It seems that built-in driver crashed some way. I try to disable switching off displays after some period of time and note if that help.

---

### Post by dbehterev on 2021-07-25
I disabled switching off all displays and it helped - the second display is still working as expected.
I afraid of use Nvidia proprietary driver because on 20.04.1 system this cause that the second display that is connected to NVidia GPU doesn't work. I tried substitute Xorg configs without success, spent a ton of time trying to understand cause of problem - without effect.
Also sometimes machine could hang and I see only green display that is connected to the AMD gpu.
I would appreciate any comments from anybody who has the same experience and could give some advice. For a long period of time I try to make my dream workspace based on Linux for development and regular usage but without success - I continue using Windows. The problems that I had on all Linux distros for ages:
- system couldn't restart by itself for some reason - hang some of service and so on. I still don't understand why it is impossible to hard code reboot process so machine always will be rebooted by user request. This problem was solved in 99% cases on Windows system.
- hybernate/suspend is still not working as expected and have many side effects like external display doesn't work or whole system hang. 
- network manager - I don't understand why /etc/network/interfaces was given up and now it is another point of problem - sometimes it hangs and all system becomes unresponsible so only hard reset is salvation.
- drivers always were Achilles' heel in Linux but now it is much better. I believe that many people don't update theirs systems for only one reason: after you invest your time to make your system to work as you want (more-less) after some update everything could be unstable or even whole system could be inappropriate for working. 
- make eToken/ruToken and other smartcards to work - is always headache.
- I don't understand why updating from 20.04.1 to 20.04.2 could be done only through full format your system but update to 20.10 could be done without losing your data and settings.

---

