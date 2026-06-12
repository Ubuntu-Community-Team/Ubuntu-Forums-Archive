---
title: "Problem with USB connect mobile phone through data cable"
date: 2009-04-28
forum: General Help
---

### Post by ppp111 on 2009-04-28
I connect mobile phone SE380i with USB data cable and have following problem in dmesg


```

[ 2836.292015] usb 3-1: new full speed USB device using uhci_hcd and address 3
[ 2836.515660] usb 3-1: configuration #2 chosen from 1 choice
[ 2836.597820] cdc_acm 3-1:2.1: ttyACM0: USB ACM device
[ 2836.601285] usbcore: registered new interface driver cdc_acm
[ 2836.601292] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
[ 2836.602335] BUG: unable to handle kernel NULL pointer dereference at 00000003
[ 2836.602343] IP: [<f7e335f5>] wdm_probe+0x165/0x410 [cdc_wdm]
[ 2836.602353] *pde = 00000000 
[ 2836.602358] Oops: 0000 [#1] SMP 
[ 2836.602363] last sysfs file: /sys/devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:2.4/interface
[ 2836.602370] Dumping ftrace buffer:
[ 2836.602374]    (ftrace buffer empty)
[ 2836.602377] Modules linked in: cdc_wdm(+) cdc_acm binfmt_misc bridge stp bnep cdahdi dahdi crc_ccitt ct cx input_polldev video output w83627ehf hwmon_vid lp snd_usb_audio snd_usb_lib snd_hwdep snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device iTCO_wdt iTCO_vendor_support cp psmouse radio_si470x ce intel_agp ppdev pcspkr cbinder snd soundcore snd_page_alloc serio_raw videodev v4l1_compat agpgart parport_pc parport usbhid floppy r8169 mii fbcon tileblit font bitblit softcursor
[ 2836.602457] 
[ 2836.602461] Pid: 5554, comm: modprobe Not tainted (2.6.28-11-generic #42-Ubuntu) MS-7176
[ 2836.602465] EIP: 0060:[<f7e335f5>] EFLAGS: 00010286 CPU: 0
[ 2836.602471] EIP is at wdm_probe+0x165/0x410 [cdc_wdm]
[ 2836.602474] EAX: 00000000 EBX: 00000800 ECX: f7e37600 EDX: f4149200
[ 2836.602478] ESI: f5c832e5 EDI: f5c83000 EBP: f5d35cf4 ESP: f5d35ca8
[ 2836.602481]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
[ 2836.602485] Process modprobe (pid: 5554, ti=f5d34000 task=f41cbed0 task.ti=f5d34000)
[ 2836.602489] Stack:
[ 2836.602491]  f5d35cb4 c01cf830 ce7ea968 f5d35cd8 c020c036 f4149200 f414921c c020b87b
[ 2836.602502]  00000000 c0501a4b f2811800 fffffff4 0800b2f4 f281185c f41492b8 f7e35394
[ 2836.602514]  f4149200 00000000 f414921c f5d35d20 c03bb942 f4149294 f5d35d0c c020c692
[ 2836.602527] Call Trace:
[ 2836.602530]  [<c01cf830>] ? iput+0x20/0x60
[ 2836.602539]  [<c020c036>] ? sysfs_addrm_finish+0x36/0xf0
[ 2836.602546]  [<c020b87b>] ? sysfs_addrm_start+0x5b/0xa0
[ 2836.602552]  [<c0501a4b>] ? mutex_lock+0xb/0x20
[ 2836.602561]  [<c03bb942>] ? usb_probe_interface+0xa2/0x130
[ 2836.602568]  [<c020c692>] ? sysfs_create_link+0x12/0x20
[ 2836.602578]  [<c034f096>] ? really_probe+0xe6/0x180
[ 2836.602584]  [<c03bada1>] ? usb_match_id+0x41/0x60
[ 2836.602594]  [<c034f16e>] ? driver_probe_device+0x3e/0x50
[ 2836.602602]  [<c034f209>] ? __driver_attach+0x89/0x90
[ 2836.602610]  [<c034e943>] ? bus_for_each_dev+0x53/0x80
[ 2836.602617]  [<c034eec9>] ? driver_attach+0x19/0x20
[ 2836.602623]  [<c034f180>] ? __driver_attach+0x0/0x90
[ 2836.602628]  [<c034e317>] ? bus_add_driver+0x1c7/0x240
[ 2836.602638]  [<c034f3a9>] ? driver_register+0x69/0x140
[ 2836.602647]  [<c03bbc0c>] ? usb_register_driver+0x7c/0x100
[ 2836.602653]  [<c020b280>] ? sysfs_ilookup_test+0x0/0x20
[ 2836.602661]  [<f7e04000>] ? wdm_init+0x0/0x19 [cdc_wdm]
[ 2836.602667]  [<f7e04017>] ? wdm_init+0x17/0x19 [cdc_wdm]
[ 2836.602673]  [<c010111e>] ? _stext+0x2e/0x170
[ 2836.602678]  [<c020c015>] ? sysfs_addrm_finish+0x15/0xf0
[ 2836.602683]  [<c020b7e3>] ? sysfs_add_one+0x13/0x50
[ 2836.602688]  [<c020b85f>] ? sysfs_addrm_start+0x3f/0xa0
[ 2836.602694]  [<c01a908c>] ? __vunmap+0x9c/0xe0
[ 2836.602700]  [<c01a908c>] ? __vunmap+0x9c/0xe0
[ 2836.602710]  [<c01a9121>] ? vfree+0x21/0x30
[ 2836.602716]  [<c0163f3a>] ? load_module+0x103a/0x1040
[ 2836.602734]  [<c0163fc8>] ? sys_init_module+0x88/0x1b0
[ 2836.602740]  [<c0103f6b>] ? sysenter_do_call+0x12/0x2f
[ 2836.602746]  [<c0500000>] ? relay_hotcpu_callback+0x6d/0xbd
[ 2836.602752] Code: 00 00 00 c7 87 9c 00 00 00 10 3c e3 f7 66 89 47 38 8d 87 94 00 00 00 89 87 94 00 00 00 89 87 98 00 00 00 8b 02 8b 40 0c 89 45 d4 <0f> b6 40 03 83 e0 03 83 f8 03 74 3f c7 45 e0 ea ff ff ff 89 f8 
[ 2836.602821] EIP: [<f7e335f5>] wdm_probe+0x165/0x410 [cdc_wdm] SS:ESP 0068:f5d35ca8
[ 2836.602832] ---[ end trace a16f9a542489aeec ]---


```

---

