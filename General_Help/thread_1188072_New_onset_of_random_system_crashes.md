---
title: "New onset of random system crashes"
date: 2009-06-15
forum: General Help
---

### Post by jharris0221 on 2009-06-15
Hey guys,

Starting about 5 days ago, my 9.04 x64 install started having some issues. The first thing I noticed is that firefox would randomly stop responding, and after forcing it to close and restarting the program, it would hang faster than the time before. Then, pidgin started doing the same thing. Finally, my whole computer would start freezing and I couldn't switch to shell. Now, I can't use my computer for more than 10 minutes before it freezes BUT it will stay on and nothing happens if I leave it alone (I used it to stream a 35-40 minute tv show to my xbox last night) Thinking back, I also had some issues where editing files in Picasa would corrupt the new file (but not the backup, thankfully)- I don't know if this is related or not.

I also tried looking through my logs to see if I could find any hints as to why this was happening. I found the following in the kernel log, is it related? Any idea what it means?

> Jun 14 19:38:34 Eagle kernel: [ 3364.168790] general protection fault: 0000 [#1] SMP
Jun 14 19:38:34 Eagle kernel: [ 3364.168794] last sysfs file: /sys/devices/pci0000:00/0000:00:1a.0/usb3/3-0:1.0/bInterfaceClass
Jun 14 19:38:34 Eagle kernel: [ 3364.168797] Dumping ftrace buffer:
Jun 14 19:38:34 Eagle kernel: [ 3364.168800]    (ftrace buffer empty)
Jun 14 19:38:34 Eagle kernel: [ 3364.168801] CPU 1
Jun 14 19:38:34 Eagle kernel: [ 3364.168803] Modules linked in: binfmt_misc ppdev bridge stp bnep vboxnetflt vboxdrv video output input_polldev ipt_REJECT ipt_LOG xt_limit xt_tcpudp xt_state ipt_addrtype ip6table_filter ip6_tables nf_nat_irc nf_conntrack_irc nf_nat_ftp nf_nat nf_conntrack_ipv4 nf_defrag_ipv4 nf_conntrack_ftp nf_conntrack iptable_filter ip_tables x_tables tun lp parport snd_hda_intel snd_usb_audio snd_pcm_oss snd_usb_lib snd_mixer_oss snd_hwdep snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq joydev snd_timer snd_seq_device snd hid_logitech ff_memless pwc iTCO_wdt iTCO_vendor_support intel_agp soundcore snd_page_alloc pcspkr compat_ioctl32 videodev v4l1_compat usbhid uinput nvidia(P) serio_raw floppy atl1 mii fbcon tileblit font bitblit softcursor
Jun 14 19:38:34 Eagle kernel: [ 3364.168847] Pid: 7519, comm: gconftool-2 Tainted: P           2.6.28-11-generic #42-Ubuntu
Jun 14 19:38:34 Eagle kernel: [ 3364.168849] RIP: 0010:[<ffffffff802ce12a>]  [<ffffffff802ce12a>] anon_vma_unlink+0x3a/0xa0
Jun 14 19:38:34 Eagle kernel: [ 3364.168856] RSP: 0018:ffff8800a6c29df8  EFLAGS: 00010246
Jun 14 19:38:34 Eagle kernel: [ 3364.168858] RAX: 7fff88011a19aae8 RBX: ffff8800a71982a0 RCX: 00007fb1472d1000
Jun 14 19:38:34 Eagle kernel: [ 3364.168860] RDX: ffff88011a19aae8 RSI: ffff880128c70580 RDI: ffff88011a19aae0
Jun 14 19:38:34 Eagle kernel: [ 3364.168862] RBP: ffff8800a6c29e18 R08: ffff880128c70580 R09: ffff8800a6c29e28
Jun 14 19:38:34 Eagle kernel: [ 3364.168864] R10: 0000000000000002 R11: 0000000000000000 R12: ffff88011a19aae0
Jun 14 19:38:34 Eagle kernel: [ 3364.168865] R13: 00007fb144299000 R14: ffff8800280388c0 R15: 0000000000000000
Jun 14 19:38:34 Eagle kernel: [ 3364.168868] FS:  0000000000000000(0000) GS:ffff88012f802b00(0000) knlGS:0000000000000000
Jun 14 19:38:34 Eagle kernel: [ 3364.168869] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Jun 14 19:38:34 Eagle kernel: [ 3364.168871] CR2: 00007fb14518f6a0 CR3: 0000000000201000 CR4: 00000000000006a0
Jun 14 19:38:34 Eagle kernel: [ 3364.168873] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Jun 14 19:38:34 Eagle kernel: [ 3364.168875] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Jun 14 19:38:34 Eagle kernel: [ 3364.168877] Process gconftool-2 (pid: 7519, threadinfo ffff8800a6c28000, task ffff88010d185980)
Jun 14 19:38:34 Eagle kernel: [ 3364.168879] Stack:
Jun 14 19:38:34 Eagle kernel: [ 3364.168880]  ffff8800a7198348 ffff8800a71982a0 00007fb144299000 ffff8800280388c0
Jun 14 19:38:34 Eagle kernel: [ 3364.168883]  ffff8800a6c29e58 ffffffff802c3c39 0000000000000000 ffff8800280388c0
Jun 14 19:38:34 Eagle kernel: [ 3364.168887]  ffff8800a71980a8 ffff8800cdd916c0 ffff8800cdd91720 ffff88010d185f78
Jun 14 19:38:34 Eagle kernel: [ 3364.168891] Call Trace:
Jun 14 19:38:34 Eagle kernel: [ 3364.168892]  [<ffffffff802c3c39>] free_pgtables+0xa9/0x110
Jun 14 19:38:34 Eagle kernel: [ 3364.168896]  [<ffffffff802c954f>] exit_mmap+0xcf/0x170
Jun 14 19:38:34 Eagle kernel: [ 3364.168898]  [<ffffffff8024eaf8>] mmput+0x38/0xd0
Jun 14 19:38:34 Eagle kernel: [ 3364.168902]  [<ffffffff80252f56>] exit_mm+0x116/0x150
Jun 14 19:38:34 Eagle kernel: [ 3364.168905]  [<ffffffff8069e471>] ? _spin_lock_irq+0x11/0x20
Jun 14 19:38:34 Eagle kernel: [ 3364.168909]  [<ffffffff80254f0c>] do_exit+0x16c/0x3b0
Jun 14 19:38:34 Eagle kernel: [ 3364.168912]  [<ffffffff80255192>] do_group_exit+0x42/0xc0
Jun 14 19:38:34 Eagle kernel: [ 3364.168915]  [<ffffffff80255222>] sys_exit_group+0x12/0x20
Jun 14 19:38:34 Eagle kernel: [ 3364.168918]  [<ffffffff8021253a>] system_call_fastpath+0x16/0x1b
Jun 14 19:38:34 Eagle kernel: [ 3364.168922] Code: 24 08 48 89 fb 4c 89 6c 24 10 4c 89 74 24 18 4c 8b 67 78 4d 85 e4 74 3f 4c 89 e7 e8 41 04 3d 00 48 8b 53 68 48 8b 43 70 4c 89 e7 <48> 89 10 48 89 42 08 48 c7 43 68 00 01 10 00 48 c7 43 70 00 02
Jun 14 19:38:34 Eagle kernel: [ 3364.168951] RIP  [<ffffffff802ce12a>] anon_vma_unlink+0x3a/0xa0
Jun 14 19:38:34 Eagle kernel: [ 3364.168954]  RSP <ffff8800a6c29df8>
Jun 14 19:38:34 Eagle kernel: [ 3364.168957] ---[ end trace 8b9600dbd6a98d04 ]---
Jun 14 19:38:34 Eagle kernel: [ 3364.168958] Fixing recursive fault but reboot is needed!

I looked through the list of common Jaunty bugs, but it doesn't seem to fit any of them to me. Perhaps it is one of the graphics driver issues? Any help would be much appreciated!

EDIT: I update my system every ~5 days and it is up to date as of last night.

---

### Post by gruntlips_ on 2009-07-03
I am having a similar problem.  My firefox and pigdin crash and the log says:

Fixing recursive fault but reboot is needed!

Any ideas since this post?

Thanks.

- gl

---

### Post by jcm1107 on 2009-07-03
I was having the same freezing of firefox too, it was like a week ago so I don't remember exactly what was causing my problem, but I do know it was because of something hogging the processor. I think I tried to kill the process but that didn't work then I tried restarting the system and that fixed it for me. So if you can safely reastart your computer without loosing anything it may fix your problem.

---

### Post by jharris0221 on 2009-07-03
I found out that some of my memory sticks were bad. Try using the memtest function on an ubuntu boot CD.

---

