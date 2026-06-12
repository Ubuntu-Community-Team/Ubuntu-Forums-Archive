---
title: "repeated &quot;BUG: unable to handle kernel NULL pointer dereference at 00000006&quot; on 9.04"
date: 2009-05-13
forum: General Help
---

### Post by belgarth on 2009-05-13
Hi all,

I am having a problem with Kernel Panics since my upgrade to 9.04 from 8.10. I did the upgrade as a fresh install which included moving from ext3 to ext4. The machine is uses an AN-M2HD motherboard with 2 GB of ram and 2 750 GB hard drives using SW Raid.

Any pointers on troubleshooting what is going on would be appreciated. I would at least like to know if the problem is specific to EXT4 because if so, it would be annoying but simple enough to format and go back to EXT3.

There have been 2 different tainted processes with different call traces. The firefox one has occurred 5 times and the Xorg one once. I am posting both since they are significantly different call traces. I don't know yet what triggers it for sure. I believe the Xorg one occurred while entering/leaving full screen mode with vlc. Today I came home and found the pc frozen due to the firefox tainted one, so it happened while I wasn't home.

syslog outputs:

May  5 22:24:18 ubuntu kernel: [ 6758.037145] BUG: unable to handle kernel NULL pointer dereference at 00000006
May  5 22:24:18 ubuntu kernel: [ 6758.037162] IP: [<c01939d5>] prep_new_page+0x25/0x140
May  5 22:24:18 ubuntu kernel: [ 6758.037178] *pde = 00000000
May  5 22:24:18 ubuntu kernel: [ 6758.037186] Oops: 0000 [#1] SMP
May  5 22:24:18 ubuntu kernel: [ 6758.037192] last sysfs file: /sys/devices/pci0000:00/0000:00:09.0/host3/target3:0:0/3:0:0:0/queue_depth
May  5 22:24:18 ubuntu kernel: [ 6758.037201] Dumping ftrace buffer:
May  5 22:24:18 ubuntu kernel: [ 6758.037207]    (ftrace buffer empty)
May  5 22:24:18 ubuntu kernel: [ 6758.037211] Modules linked in: nls_iso8859_1 nls_cp437 vfat fat binfmt_misc ppdev bridge stp bnep input_p\
olldev video output lp parport snd_hda_codec_nvhdmi snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss t\
uner_simple snd_pcm tuner_types snd_seq_dummy snd_seq_oss snd_seq_midi wm8775 snd_rawmidi snd_seq_midi_event cx25840 snd_seq snd_timer snd_\
seq_device tuner ivtv snd nvidia(P) compat_ioctl32 i2c_algo_bit k8temp soundcore snd_page_alloc pcspkr agpgart pl2303 cx2341x v4l2_common v\
ideodev v4l1_compat tveeprom joydev hid_gyration usbhid forcedeth ohci1394 ieee1394 floppy raid10 usb_storage raid456 async_xor async_memcp\
y async_tx xor raid1 raid0 multipath linear fbcon tileblit font bitblit softcursor
May  5 22:24:18 ubuntu kernel: [ 6758.037305]
May  5 22:24:18 ubuntu kernel: [ 6758.037312] Pid: 3296, comm: Xorg Tainted: P           (2.6.28-11-generic #42-Ubuntu) .
May  5 22:24:18 ubuntu kernel: [ 6758.037317] EIP: 0060:[<c01939d5>] EFLAGS: 00213202 CPU: 0
May  5 22:24:18 ubuntu kernel: [ 6758.037324] EIP is at prep_new_page+0x25/0x140
May  5 22:24:18 ubuntu kernel: [ 6758.037328] EAX: 00000002 EBX: 00000000 ECX: 90f2edc8 EDX: c10008a0
May  5 22:24:18 ubuntu kernel: [ 6758.037333] ESI: ffffffff EDI: c06d0f80 EBP: f2a7bd04 ESP: f2a7bce4
May  5 22:24:18 ubuntu kernel: [ 6758.037337]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
May  5 22:24:18 ubuntu kernel: [ 6758.037342] Process Xorg (pid: 3296, ti=f2a7a000 task=f2881920 task.ti=f2a7a000)
May  5 22:24:18 ubuntu kernel: [ 6758.037346] Stack:
May  5 22:24:18 ubuntu kernel: [ 6758.037349]  f2a7bd04 001280d2 00000000 c10008a0 c06d0f80 c10008a0 c06d100c c06d0f80
May  5 22:24:18 ubuntu kernel: [ 6758.037362]  f2a7bd40 c0193c92 c06d100c 00000002 c07b8040 00000080 00000000 00000000
May  5 22:24:18 ubuntu kernel: [ 6758.037373]  c06d3000 00203246 00000002 00000001 c06d0f80 00000000 c06d9f94 f2a7bd80
May  5 22:24:18 ubuntu kernel: [ 6758.037386] Call Trace:
May  5 22:24:18 ubuntu kernel: [ 6758.037390]  [<c0193c92>] ? buffered_rmqueue+0x1a2/0x2a0
May  5 22:24:18 ubuntu kernel: [ 6758.037398]  [<c0193e4b>] ? get_page_from_freelist+0xbb/0x150
May  5 22:24:18 ubuntu kernel: [ 6758.037405]  [<c0193f99>] ? __alloc_pages_internal+0xb9/0x490
May  5 22:24:18 ubuntu kernel: [ 6758.037412]  [<c01a78a9>] ? anon_vma_prepare+0x19/0xc0
May  5 22:24:18 ubuntu kernel: [ 6758.037421]  [<c019c108>] ? __inc_zone_page_state+0x18/0x20
May  5 22:24:18 ubuntu kernel: [ 6758.037430]  [<c019fa07>] ? do_anonymous_page+0x47/0x1d0
May  5 22:24:18 ubuntu kernel: [ 6758.037437]  [<c0127453>] ? kmap_atomic_prot+0x43/0xe0
May  5 22:24:18 ubuntu kernel: [ 6758.037445]  [<c01a1faf>] ? handle_mm_fault+0x2af/0x380
May  5 22:24:18 ubuntu kernel: [ 6758.037451]  [<c0105318>] ? apic_timer_interrupt+0x28/0x30
May  5 22:24:18 ubuntu kernel: [ 6758.037459]  [<c050521d>] ? do_page_fault+0x1fd/0x790
May  5 22:24:18 ubuntu kernel: [ 6758.037470]  [<c010bb1f>] ? restore_i387_xstate+0xff/0x210
May  5 22:24:18 ubuntu kernel: [ 6758.037476]  [<c0103c56>] ? handle_signal+0xf6/0x190
May  5 22:24:18 ubuntu kernel: [ 6758.037483]  [<c0103dc6>] ? do_notify_resume+0xd6/0x190
May  5 22:24:18 ubuntu kernel: [ 6758.037490]  [<c0103130>] ? restore_sigcontext+0x100/0x150
May  5 22:24:18 ubuntu kernel: [ 6758.037496]  [<c0103383>] ? sys_sigreturn+0xe3/0x190
May  5 22:24:18 ubuntu kernel: [ 6758.037503]  [<c01cc65d>] ? sys_select+0x3d/0xb0
May  5 22:24:18 ubuntu kernel: [ 6758.037511]  [<c05033b0>] ? do_device_not_available+0x0/0x60
May  5 22:24:18 ubuntu kernel: [ 6758.037519]  [<c0505020>] ? do_page_fault+0x0/0x790
May  5 22:24:18 ubuntu kernel: [ 6758.037525]  [<c0503082>] ? error_code+0x72/0x80
May  5 22:24:18 ubuntu kernel: [ 6758.037532] Code: 8d bf 00 00 00 00 55 89 e5 57 56 53 83 ec 14 89 45 ec 89 55 e8 89 4d e4 8b 08 8b 70 08 \
8b 58 10 f6 c5 40 74 06 8b 55 ec 8b 42 0c <8b> 40 04 85 c0 0f 95 c2 85 db 0f 95 c0 09 d0 83 e0 01 8d 56 01
May  5 22:24:18 ubuntu kernel: [ 6758.037592] EIP: [<c01939d5>] prep_new_page+0x25/0x140 SS:ESP 0068:f2a7bce4
May  5 22:24:18 ubuntu kernel: [ 6758.037603] ---[ end trace dd75f60d37dc5a83 ]---


May  5 22:20:02 ubuntu /USR/SBIN/CRON[13619]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
May  5 22:24:18 ubuntu kernel: [ 6758.037145] BUG: unable to handle kernel NULL pointer dereference at 00000006
May  5 22:24:18 ubuntu kernel: [ 6758.037162] IP: [<c01939d5>] prep_new_page+0x25/0x140
May  5 22:24:18 ubuntu kernel: [ 6758.037178] *pde = 00000000
May  5 22:24:18 ubuntu kernel: [ 6758.037186] Oops: 0000 [#1] SMP
May  5 22:24:18 ubuntu kernel: [ 6758.037192] last sysfs file: /sys/devices/pci0000:00/0000:00:09.0/host3/target3:0:0/3:0:0:0/queue_depth
May  5 22:24:18 ubuntu kernel: [ 6758.037201] Dumping ftrace buffer:
May  5 22:24:18 ubuntu kernel: [ 6758.037207]    (ftrace buffer empty)
May  5 22:24:18 ubuntu kernel: [ 6758.037211] Modules linked in: nls_iso8859_1 nls_cp437 vfat fat binfmt_misc ppdev bridge stp bnep input_p\
olldev video output lp parport snd_hda_codec_nvhdmi snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss t\
uner_simple snd_pcm tuner_types snd_seq_dummy snd_seq_oss snd_seq_midi wm8775 snd_rawmidi snd_seq_midi_event cx25840 snd_seq snd_timer snd_\
seq_device tuner ivtv snd nvidia(P) compat_ioctl32 i2c_algo_bit k8temp soundcore snd_page_alloc pcspkr agpgart pl2303 cx2341x v4l2_common v\
ideodev v4l1_compat tveeprom joydev hid_gyration usbhid forcedeth ohci1394 ieee1394 floppy raid10 usb_storage raid456 async_xor async_memcp\
y async_tx xor raid1 raid0 multipath linear fbcon tileblit font bitblit softcursor
May  5 22:24:18 ubuntu kernel: [ 6758.037305]
May  5 22:24:18 ubuntu kernel: [ 6758.037312] Pid: 3296, comm: Xorg Tainted: P           (2.6.28-11-generic #42-Ubuntu) .
May  5 22:24:18 ubuntu kernel: [ 6758.037317] EIP: 0060:[<c01939d5>] EFLAGS: 00213202 CPU: 0
May  5 22:24:18 ubuntu kernel: [ 6758.037324] EIP is at prep_new_page+0x25/0x140
May  5 22:24:18 ubuntu kernel: [ 6758.037328] EAX: 00000002 EBX: 00000000 ECX: 90f2edc8 EDX: c10008a0
May  5 22:24:18 ubuntu kernel: [ 6758.037333] ESI: ffffffff EDI: c06d0f80 EBP: f2a7bd04 ESP: f2a7bce4
May  5 22:24:18 ubuntu kernel: [ 6758.037337]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
May  5 22:24:18 ubuntu kernel: [ 6758.037342] Process Xorg (pid: 3296, ti=f2a7a000 task=f2881920 task.ti=f2a7a000)
May  5 22:24:18 ubuntu kernel: [ 6758.037346] Stack:
May  5 22:24:18 ubuntu kernel: [ 6758.037349]  f2a7bd04 001280d2 00000000 c10008a0 c06d0f80 c10008a0 c06d100c c06d0f80
May  5 22:24:18 ubuntu kernel: [ 6758.037362]  f2a7bd40 c0193c92 c06d100c 00000002 c07b8040 00000080 00000000 00000000
May  5 22:24:18 ubuntu kernel: [ 6758.037373]  c06d3000 00203246 00000002 00000001 c06d0f80 00000000 c06d9f94 f2a7bd80
May  5 22:24:18 ubuntu kernel: [ 6758.037386] Call Trace:
May  5 22:24:18 ubuntu kernel: [ 6758.037390]  [<c0193c92>] ? buffered_rmqueue+0x1a2/0x2a0
May  5 22:24:18 ubuntu kernel: [ 6758.037398]  [<c0193e4b>] ? get_page_from_freelist+0xbb/0x150
May  5 22:24:18 ubuntu kernel: [ 6758.037405]  [<c0193f99>] ? __alloc_pages_internal+0xb9/0x490
May  5 22:24:18 ubuntu kernel: [ 6758.037412]  [<c01a78a9>] ? anon_vma_prepare+0x19/0xc0
May  5 22:24:18 ubuntu kernel: [ 6758.037421]  [<c019c108>] ? __inc_zone_page_state+0x18/0x20
May  5 22:24:18 ubuntu kernel: [ 6758.037430]  [<c019fa07>] ? do_anonymous_page+0x47/0x1d0
May  5 22:24:18 ubuntu kernel: [ 6758.037437]  [<c0127453>] ? kmap_atomic_prot+0x43/0xe0
May  5 22:24:18 ubuntu kernel: [ 6758.037445]  [<c01a1faf>] ? handle_mm_fault+0x2af/0x380
May  5 22:24:18 ubuntu kernel: [ 6758.037451]  [<c0105318>] ? apic_timer_interrupt+0x28/0x30
May  5 22:24:18 ubuntu kernel: [ 6758.037459]  [<c050521d>] ? do_page_fault+0x1fd/0x790
May  5 22:24:18 ubuntu kernel: [ 6758.037470]  [<c010bb1f>] ? restore_i387_xstate+0xff/0x210
May  5 22:24:18 ubuntu kernel: [ 6758.037476]  [<c0103c56>] ? handle_signal+0xf6/0x190
May  5 22:24:18 ubuntu kernel: [ 6758.037483]  [<c0103dc6>] ? do_notify_resume+0xd6/0x190
May  5 22:24:18 ubuntu kernel: [ 6758.037490]  [<c0103130>] ? restore_sigcontext+0x100/0x150
May  5 22:24:18 ubuntu kernel: [ 6758.037496]  [<c0103383>] ? sys_sigreturn+0xe3/0x190
May  5 22:24:18 ubuntu kernel: [ 6758.037503]  [<c01cc65d>] ? sys_select+0x3d/0xb0
May  5 22:24:18 ubuntu kernel: [ 6758.037511]  [<c05033b0>] ? do_device_not_available+0x0/0x60
May  5 22:24:18 ubuntu kernel: [ 6758.037519]  [<c0505020>] ? do_page_fault+0x0/0x790
May  5 22:24:18 ubuntu kernel: [ 6758.037525]  [<c0503082>] ? error_code+0x72/0x80
May  5 22:24:18 ubuntu kernel: [ 6758.037532] Code: 8d bf 00 00 00 00 55 89 e5 57 56 53 83 ec 14 89 45 ec 89 55 e8 89 4d e4 8b 08 8b 70 08 \
8b 58 10 f6 c5 40 74 06 8b 55 ec 8b 42 0c <8b> 40 04 85 c0 0f 95 c2 85 db 0f 95 c0 09 d0 83 e0 01 8d 56 01
May  5 22:24:18 ubuntu kernel: [ 6758.037592] EIP: [<c01939d5>] prep_new_page+0x25/0x140 SS:ESP 0068:f2a7bce4
May  5 22:24:18 ubuntu kernel: [ 6758.037603] ---[ end trace dd75f60d37dc5a83 ]---

---

