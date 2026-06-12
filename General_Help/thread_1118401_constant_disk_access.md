---
title: "constant disk access"
date: 2009-04-06
forum: General Help
---

### Post by strider22 on 2009-04-06
My system randomly undergoes constant disk accesses to the point where it is unusable. 

At 11:14 on April 05 the access started. The clock was still saying 11:14 when I went to bed. The system was ok at 7:00 in the morning on April 06 but when I got home at 5:55 and woke up the system, the disk access started again. by 10:30 the clock still said 5:55! I don't know if it was 5:55 am or pm. Therefore I have included the whole system log for the day. It's not huge.

I could not pull down the system menu. I managed to get an open terminal to come to the front and typed ntop but after 2 hours the command still had not executed. Control Alt backspace eventually forced a log out.

I am using Hardy Heron Ubuntu 8.04
The problem initially seemed to be related to using rhythmbox but I have told it to allow 90% free cpu and to minimize memory usage and not to watch the directories. There is about 30gig of songs indexed on the usb drive and about 12gig on the laptop drive. (many duplicates from copying) The problem seemed to go away for about a week after making those changes.

Here is the system log messages; (tell me if you want any other info) (I have saved dmesg)
I expect the Marks from 7:55 to 22:16 are the clock catching up after the logout and login.
```

Apr  6 00:15:20 beryllium -- MARK --
Apr  6 00:35:42 beryllium -- MARK --
Apr  6 00:40:43 beryllium kernel: [26792.391392] hal-ipw-killswi[25172]: segfault at 00000000 eip 08048beb esp bfe51840 error 4
Apr  6 00:44:35 beryllium kernel: [27024.717219] hal-ipw-killswi[25192]: segfault at 00000000 eip 08048beb esp bfef5710 error 4
Apr  6 00:56:16 beryllium -- MARK --
Apr  6 01:15:52 beryllium kernel: [28885.028944] hal-ipw-killswi[25288]: segfault at 00000000 eip 08048beb esp bf80c390 error 4
Apr  6 01:30:00 beryllium kernel: [29750.996311] hal-ipw-killswi[25320]: segfault at 00000000 eip 08048beb esp bfe55670 error 4
Apr  6 01:39:01 beryllium kernel: [30291.750356] hal-ipw-killswi[25334]: segfault at 00000000 eip 08048beb esp bfd78940 error 4
Apr  6 01:57:57 beryllium -- MARK --
Apr  6 02:08:34 beryllium kernel: [32059.597340] hal-ipw-killswi[25382]: segfault at 00000000 eip 08048beb esp bfbe8500 error 4
Apr  6 02:39:17 beryllium -- MARK --
Apr  6 02:56:46 beryllium kernel: [34942.605635] hal-ipw-killswi[25476]: segfault at 00000000 eip 08048beb esp bff4c870 error 4
Apr  6 03:01:34 beryllium kernel: [35241.171630] hal-ipw-killswi[25483]: segfault at 00000000 eip 08048beb esp bfe666d0 error 4
Apr  6 03:20:45 beryllium -- MARK --
Apr  6 03:41:25 beryllium -- MARK --
Apr  6 03:56:29 beryllium gnome-power-manager: (chris) Suspending computer. Reason: System idle.
Apr  6 03:58:03 beryllium kernel: [38629.462944] hal-ipw-killswi[25582]: segfault at 00000000 eip 08048beb esp bfe56130 error 4
Apr  6 04:08:52 beryllium kernel: [39277.243493] hal-ipw-killswi[25598]: segfault at 00000000 eip 08048beb esp bf8c0b30 error 4
Apr  6 04:19:22 beryllium kernel: [39906.384736] hal-ipw-killswi[25619]: segfault at 00000000 eip 08048beb esp bfc51c70 error 4
Apr  6 04:22:48 beryllium kernel: [40109.917933] hal-ipw-killswi[25627]: segfault at 00000000 eip 08048beb esp bff46900 error 4
Apr  6 04:27:02 beryllium kernel: [40365.767390] hal-ipw-killswi[25631]: segfault at 00000000 eip 08048beb esp bfbc9610 error 4
Apr  6 04:37:43 beryllium gnome-power-manager: (chris) Resuming computer
Apr  6 04:38:18 beryllium kernel: [41042.127803] hal-ipw-killswi[25651]: segfault at 00000000 eip 08048beb esp bff0dee0 error 4
Apr  6 04:40:40 beryllium kernel: [41181.411995] hal-ipw-killswi[25662]: segfault at 00000000 eip 08048beb esp bfe906a0 error 4
Apr  6 05:04:05 beryllium -- MARK --
Apr  6 05:24:15 beryllium kernel: [43795.489956] hal-ipw-killswi[25748]: segfault at 00000000 eip 08048beb esp bfc66990 error 4
Apr  6 05:27:16 beryllium kernel: [43976.867955] hal-ipw-killswi[25752]: segfault at 00000000 eip 08048beb esp bfdd5700 error 4
Apr  6 05:44:19 beryllium kernel: [45000.898722] hal-ipw-killswi[25780]: segfault at 00000000 eip 08048beb esp bfaaf2c0 error 4
Apr  6 05:54:38 beryllium kernel: [45600.921738] hal-ipw-killswi[25790]: segfault at 00000000 eip 08048beb esp bf9e3200 error 4
Apr  6 06:06:29 beryllium -- MARK --
Apr  6 06:21:13 beryllium kernel: [47206.834398] hal-ipw-killswi[25819]: segfault at 00000000 eip 08048beb esp bf984c40 error 4
Apr  6 06:47:45 beryllium -- MARK --
Apr  6 06:51:12 beryllium kernel: [49008.558680] hal-ipw-killswi[25853]: segfault at 00000000 eip 08048beb esp bfc29b50 error 4
Apr  6 07:08:19 beryllium -- MARK --
Apr  6 07:29:06 beryllium -- MARK --
Apr  6 07:45:23 beryllium kernel: [52259.740737] dbus-daemon invoked oom-killer: gfp_mask=0x1201d2, order=0, oomkilladj=0
Apr  6 07:45:23 beryllium kernel: [52259.740751] Pid: 5145, comm: dbus-daemon Not tainted 2.6.24-23-generic #1
Apr  6 07:45:23 beryllium kernel: [52259.740792]  [oom_kill_process+0x10a/0x120] oom_kill_process+0x10a/0x120
Apr  6 07:45:23 beryllium kernel: [52259.740856]  [out_of_memory+0x167/0x1a0] out_of_memory+0x167/0x1a0
Apr  6 07:45:23 beryllium kernel: [52259.740910]  [agpgart:__alloc_pages+0x36c/0x3a0] __alloc_pages+0x36c/0x3a0
Apr  6 07:45:23 beryllium kernel: [52259.740978]  [__do_page_cache_readahead+0x11d/0x250] __do_page_cache_readahead+0x11d/0x250
Apr  6 07:45:23 beryllium kernel: [52259.740987]  [sync_page+0x0/0x40] sync_page+0x0/0x40
Apr  6 07:45:23 beryllium kernel: [52259.741056]  [do_page_cache_readahead+0x4c/0x70] do_page_cache_readahead+0x4c/0x70
Apr  6 07:45:23 beryllium kernel: [52259.741088]  [filemap_fault+0x2f4/0x420] filemap_fault+0x2f4/0x420
Apr  6 07:45:23 beryllium kernel: [52259.741154]  [__do_fault+0x61/0x420] __do_fault+0x61/0x420
Apr  6 07:45:23 beryllium kernel: [52259.741173]  [ext3:do_sync_read+0xd5/0xba0] do_sync_read+0xd5/0x120
Apr  6 07:45:23 beryllium kernel: [52259.741220]  [libata:kunmap_atomic+0x3d/0x2f40] kunmap_atomic+0x3d/0xb0
Apr  6 07:45:23 beryllium kernel: [52259.741245]  [handle_mm_fault+0x118/0x730] handle_mm_fault+0x118/0x730
Apr  6 07:45:23 beryllium kernel: [52259.741326]  [do_page_fault+0x13f/0x730] do_page_fault+0x13f/0x730
Apr  6 07:45:23 beryllium kernel: [52259.741351]  [vfs_read+0x15f/0x170] vfs_read+0x15f/0x170
Apr  6 07:45:23 beryllium kernel: [52259.741397]  [do_page_fault+0x0/0x730] do_page_fault+0x0/0x730
Apr  6 07:45:23 beryllium kernel: [52259.741410]  [error_code+0x72/0x80] error_code+0x72/0x80
Apr  6 07:45:23 beryllium kernel: [52259.741444]  [unix_stream_recvmsg+0x3c0/0x550] unix_stream_recvmsg+0x3c0/0x550
Apr  6 07:45:23 beryllium kernel: [52259.741476]  =======================
Apr  6 07:45:23 beryllium kernel: [52259.741479] Mem-info:
Apr  6 07:45:23 beryllium kernel: [52259.741482] DMA per-cpu:
Apr  6 07:45:24 beryllium kernel: [52259.741488] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Apr  6 07:45:24 beryllium kernel: [52259.741495] CPU    1: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Apr  6 07:45:24 beryllium kernel: [52259.741500] Normal per-cpu:
Apr  6 07:45:24 beryllium kernel: [52259.741506] CPU    0: Hot: hi:  186, btch:  31 usd: 173   Cold: hi:   62, btch:  15 usd:  14
Apr  6 07:45:24 beryllium kernel: [52259.741514] CPU    1: Hot: hi:  186, btch:  31 usd: 118   Cold: hi:   62, btch:  15 usd:   2
Apr  6 07:45:24 beryllium kernel: [52259.741519] HighMem per-cpu:
Apr  6 07:45:24 beryllium kernel: [52259.741524] CPU    0: Hot: hi:   42, btch:   7 usd:  36   Cold: hi:   14, btch:   3 usd:  12
Apr  6 07:45:24 beryllium kernel: [52259.741531] CPU    1: Hot: hi:   42, btch:   7 usd:  37   Cold: hi:   14, btch:   3 usd:   6
Apr  6 07:45:24 beryllium kernel: [52259.741540] Active:205571 inactive:10478 dirty:0 writeback:0 unstable:0
Apr  6 07:45:24 beryllium kernel: [52259.741543]  free:2906 slab:3299 mapped:47 pagetables:941 bounce:0
Apr  6 07:45:24 beryllium kernel: [52259.741552] DMA free:4016kB min:68kB low:84kB high:100kB active:8212kB inactive:0kB present:16256kB pages_scanned:569742 all_unreclaimable? yes
Apr  6 07:45:24 beryllium kernel: [52259.741559] lowmem_reserve[]: 0 873 990 990
Apr  6 07:45:24 beryllium kernel: [52259.741571] Normal free:7476kB min:3744kB low:4680kB high:5616kB active:725356kB inactive:13688kB present:894080kB pages_scanned:2624422 all_unreclaimable? yes
Apr  6 07:45:24 beryllium kernel: [52259.741578] lowmem_reserve[]: 0 0 940 940
Apr  6 07:45:24 beryllium kernel: [52259.741589] HighMem free:132kB min:128kB low:252kB high:380kB active:88600kB inactive:28284kB present:120396kB pages_scanned:312810 all_unreclaimable? yes
Apr  6 07:45:24 beryllium kernel: [52259.741596] lowmem_reserve[]: 0 0 0 0
Apr  6 07:45:24 beryllium kernel: [52259.741604] DMA: 0*4kB 0*8kB 1*16kB 1*32kB 0*64kB 1*128kB 1*256kB 1*512kB 1*1024kB 1*2048kB 0*4096kB = 4016kB
Apr  6 07:45:24 beryllium kernel: [52259.741624] Normal: 803*4kB 24*8kB 1*16kB 2*32kB 1*64kB 0*128kB 1*256kB 1*512kB 1*1024kB 1*2048kB 0*4096kB = 7388kB
Apr  6 07:45:24 beryllium kernel: [52259.741643] HighMem: 18*4kB 1*8kB 1*16kB 0*32kB 1*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 160kB
Apr  6 07:45:24 beryllium kernel: [52259.741664] Swap cache: add 0, delete 0, find 0/0, race 0+0
Apr  6 07:45:24 beryllium kernel: [52259.741668] Free swap  = 0kB
Apr  6 07:45:24 beryllium kernel: [52259.741671] Total swap = 0kB
Apr  6 07:45:24 beryllium kernel: [52259.741674] Free swap:            0kB
Apr  6 07:45:24 beryllium kernel: [52259.750800] 259712 pages of RAM
Apr  6 07:45:24 beryllium kernel: [52259.750804] 30336 pages of HIGHMEM
Apr  6 07:45:24 beryllium kernel: [52259.750808] 3284 reserved pages
Apr  6 07:45:24 beryllium kernel: [52259.750811] 33241 pages shared
Apr  6 07:45:24 beryllium kernel: [52259.750814] 0 pages swap cached
Apr  6 07:45:24 beryllium kernel: [52259.750817] 0 pages dirty
Apr  6 07:45:24 beryllium kernel: [52259.750820] 0 pages writeback
Apr  6 07:45:24 beryllium kernel: [52259.750823] 47 pages mapped
Apr  6 07:45:24 beryllium kernel: [52259.750826] 3299 pages slab
Apr  6 07:45:24 beryllium kernel: [52259.750829] 941 pages pagetables
Apr  6 07:45:24 beryllium kernel: [52259.754219] dbus-daemon invoked oom-killer: gfp_mask=0x1201d2, order=0, oomkilladj=0
Apr  6 07:45:24 beryllium kernel: [52259.754230] Pid: 5145, comm: dbus-daemon Not tainted 2.6.24-23-generic #1
Apr  6 07:45:24 beryllium kernel: [52259.754268]  [oom_kill_process+0x10a/0x120] oom_kill_process+0x10a/0x120
Apr  6 07:45:24 beryllium kernel: [52259.754327]  [out_of_memory+0x167/0x1a0] out_of_memory+0x167/0x1a0
Apr  6 07:45:24 beryllium kernel: [52259.754375]  [agpgart:__alloc_pages+0x36c/0x3a0] __alloc_pages+0x36c/0x3a0
Apr  6 07:45:24 beryllium kernel: [52259.754441]  [__do_page_cache_readahead+0x11d/0x250] __do_page_cache_readahead+0x11d/0x250
Apr  6 07:45:24 beryllium kernel: [52259.754450]  [sync_page+0x0/0x40] sync_page+0x0/0x40
Apr  6 07:45:24 beryllium kernel: [52259.754518]  [do_page_cache_readahead+0x4c/0x70] do_page_cache_readahead+0x4c/0x70
Apr  6 07:45:24 beryllium kernel: [52259.754548]  [filemap_fault+0x2f4/0x420] filemap_fault+0x2f4/0x420
Apr  6 07:45:24 beryllium kernel: [52259.754612]  [__do_fault+0x61/0x420] __do_fault+0x61/0x420
Apr  6 07:45:24 beryllium kernel: [52259.754631]  [ext3:do_sync_read+0xd5/0xba0] do_sync_read+0xd5/0x120
Apr  6 07:45:24 beryllium kernel: [52259.754678]  [libata:kunmap_atomic+0x3d/0x2f40] kunmap_atomic+0x3d/0xb0
Apr  6 07:45:24 beryllium kernel: [52259.754702]  [handle_mm_fault+0x118/0x730] handle_mm_fault+0x118/0x730
Apr  6 07:45:24 beryllium kernel: [52259.754784]  [do_page_fault+0x13f/0x730] do_page_fault+0x13f/0x730
Apr  6 07:45:24 beryllium kernel: [52259.754809]  [vfs_read+0x15f/0x170] vfs_read+0x15f/0x170
Apr  6 07:45:24 beryllium kernel: [52259.754858]  [do_page_fault+0x0/0x730] do_page_fault+0x0/0x730
Apr  6 07:45:24 beryllium kernel: [52259.754871]  [error_code+0x72/0x80] error_code+0x72/0x80
Apr  6 07:45:24 beryllium kernel: [52259.754911]  [unix_stream_recvmsg+0x3c0/0x550] unix_stream_recvmsg+0x3c0/0x550
Apr  6 07:45:24 beryllium kernel: [52259.754947]  =======================
Apr  6 07:45:24 beryllium kernel: [52259.754950] Mem-info:
Apr  6 07:45:24 beryllium kernel: [52259.754953] DMA per-cpu:
Apr  6 07:45:24 beryllium kernel: [52259.754958] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Apr  6 07:45:24 beryllium kernel: [52259.754965] CPU    1: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Apr  6 07:45:24 beryllium kernel: [52259.754971] Normal per-cpu:
Apr  6 07:45:24 beryllium kernel: [52259.754976] CPU    0: Hot: hi:  186, btch:  31 usd: 173   Cold: hi:   62, btch:  15 usd:  14
Apr  6 07:45:24 beryllium kernel: [52259.754984] CPU    1: Hot: hi:  186, btch:  31 usd: 118   Cold: hi:   62, btch:  15 usd:   2
Apr  6 07:45:24 beryllium kernel: [52259.754989] HighMem per-cpu:
Apr  6 07:45:24 beryllium kernel: [52259.754994] CPU    0: Hot: hi:   42, btch:   7 usd:  36   Cold: hi:   14, btch:   3 usd:   2
Apr  6 07:45:24 beryllium kernel: [52259.755001] CPU    1: Hot: hi:   42, btch:   7 usd:  37   Cold: hi:   14, btch:   3 usd:   6
Apr  6 07:45:24 beryllium kernel: [52259.755010] Active:204645 inactive:11449 dirty:0 writeback:0 unstable:0
Apr  6 07:45:24 beryllium kernel: [52259.755013]  free:2901 slab:3299 mapped:47 pagetables:941 bounce:0
Apr  6 07:45:24 beryllium kernel: [52259.755022] DMA free:4016kB min:68kB low:84kB high:100kB active:8212kB inactive:0kB present:16256kB pages_scanned:569742 all_unreclaimable? yes
Apr  6 07:45:24 beryllium kernel: [52259.755029] lowmem_reserve[]: 0 873 990 990
Apr  6 07:45:24 beryllium kernel: [52259.755041] Normal free:7476kB min:3744kB low:4680kB high:5616kB active:725456kB inactive:13600kB present:894080kB pages_scanned:2624904 all_unreclaimable? yes
Apr  6 07:45:24 beryllium kernel: [52259.755048] lowmem_reserve[]: 0 0 940 940
Apr  6 07:45:24 beryllium kernel: [52259.755059] HighMem free:112kB min:128kB low:252kB high:380kB active:84912kB inactive:32196kB present:120396kB pages_scanned:330290 all_unreclaimable? yes
Apr  6 07:45:24 beryllium kernel: [52259.755066] lowmem_reserve[]: 0 0 0 0
Apr  6 07:45:24 beryllium kernel: [52259.755074] DMA: 0*4kB 0*8kB 1*16kB 1*32kB 0*64kB 1*128kB 1*256kB 1*512kB 1*1024kB 1*2048kB 0*4096kB = 4016kB
Apr  6 07:45:24 beryllium kernel: [52259.755093] Normal: 803*4kB 24*8kB 1*16kB 2*32kB 1*64kB 0*128kB 1*256kB 1*512kB 1*1024kB 1*2048kB 0*4096kB = 7388kB
Apr  6 07:45:24 beryllium kernel: [52259.755112] HighMem: 9*4kB 1*8kB 1*16kB 0*32kB 1*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 124kB
Apr  6 07:45:24 beryllium kernel: [52259.755133] Swap cache: add 0, delete 0, find 0/0, race 0+0
Apr  6 07:45:24 beryllium kernel: [52259.755137] Free swap  = 0kB
Apr  6 07:45:24 beryllium kernel: [52259.755140] Total swap = 0kB
Apr  6 07:45:24 beryllium kernel: [52259.755143] Free swap:            0kB
Apr  6 07:45:24 beryllium kernel: [52259.764252] 259712 pages of RAM
Apr  6 07:45:24 beryllium kernel: [52259.764256] 30336 pages of HIGHMEM
Apr  6 07:45:24 beryllium kernel: [52259.764259] 3284 reserved pages
Apr  6 07:45:24 beryllium kernel: [52259.764263] 33263 pages shared
Apr  6 07:45:24 beryllium kernel: [52259.764266] 0 pages swap cached
Apr  6 07:45:24 beryllium kernel: [52259.764269] 0 pages dirty
Apr  6 07:45:24 beryllium kernel: [52259.764272] 0 pages writeback
Apr  6 07:45:24 beryllium kernel: [52259.764275] 47 pages mapped
Apr  6 07:45:24 beryllium kernel: [52259.764278] 3299 pages slab
Apr  6 07:45:24 beryllium kernel: [52259.764281] 941 pages pagetables
Apr  6 07:55:06 beryllium syslogd 1.5.0#1ubuntu1: restart.
Apr  6 08:10:10 beryllium -- MARK --
Apr  6 08:30:10 beryllium -- MARK --
Apr  6 08:50:10 beryllium -- MARK --
Apr  6 09:10:10 beryllium -- MARK --
Apr  6 09:30:10 beryllium -- MARK --
Apr  6 09:50:10 beryllium -- MARK --
Apr  6 10:10:10 beryllium -- MARK --
Apr  6 10:30:10 beryllium -- MARK --
Apr  6 10:50:10 beryllium -- MARK --
Apr  6 11:10:11 beryllium -- MARK --
Apr  6 11:30:11 beryllium -- MARK --
Apr  6 11:50:11 beryllium -- MARK --
Apr  6 12:10:11 beryllium -- MARK --
Apr  6 12:30:11 beryllium -- MARK --
Apr  6 12:50:11 beryllium -- MARK --
Apr  6 13:10:11 beryllium -- MARK --
Apr  6 13:30:11 beryllium -- MARK --
Apr  6 13:50:15 beryllium -- MARK --
Apr  6 14:10:25 beryllium -- MARK --
Apr  6 14:30:37 beryllium -- MARK --
Apr  6 14:50:48 beryllium -- MARK --
Apr  6 15:10:59 beryllium -- MARK --
Apr  6 15:31:11 beryllium -- MARK --
Apr  6 15:51:23 beryllium -- MARK --
Apr  6 16:11:31 beryllium -- MARK --
Apr  6 16:31:43 beryllium -- MARK --
Apr  6 16:51:53 beryllium -- MARK --
Apr  6 17:12:02 beryllium -- MARK --
Apr  6 17:32:13 beryllium -- MARK --
Apr  6 17:52:25 beryllium -- MARK --
Apr  6 18:12:40 beryllium -- MARK --
Apr  6 18:32:58 beryllium -- MARK --
Apr  6 18:53:17 beryllium -- MARK --
Apr  6 19:13:37 beryllium -- MARK --
Apr  6 19:33:55 beryllium -- MARK --
Apr  6 19:54:12 beryllium -- MARK --
Apr  6 20:14:32 beryllium -- MARK --
Apr  6 20:34:52 beryllium -- MARK --
Apr  6 20:55:39 beryllium -- MARK --
Apr  6 21:16:40 beryllium -- MARK --
Apr  6 21:37:50 beryllium -- MARK --
Apr  6 21:59:10 beryllium -- MARK --
Apr  6 22:16:33 beryllium kernel: [104497.072926] rhythmbox invoked oom-killer: gfp_mask=0x1201d2, order=0, oomkilladj=0
Apr  6 22:16:34 beryllium kernel: [104497.072934] Pid: 14615, comm: rhythmbox Not tainted 2.6.24-23-generic #1
Apr  6 22:16:34 beryllium kernel: [104497.072966]  [oom_kill_process+0x10a/0x120] oom_kill_process+0x10a/0x120
Apr  6 22:16:34 beryllium kernel: [104497.073007]  [out_of_memory+0x167/0x1a0] out_of_memory+0x167/0x1a0
Apr  6 22:16:34 beryllium kernel: [104497.073044]  [agpgart:__alloc_pages+0x36c/0x3a0] __alloc_pages+0x36c/0x3a0
Apr  6 22:16:34 beryllium kernel: [104497.073093]  [filemap_fault+0x109/0x420] filemap_fault+0x109/0x420
Apr  6 22:16:34 beryllium kernel: [104497.073136]  [__do_fault+0x61/0x420] __do_fault+0x61/0x420
Apr  6 22:16:34 beryllium kernel: [104497.073171]  [libata:kunmap_atomic+0x3d/0x2f40] kunmap_atomic+0x3d/0xb0
Apr  6 22:16:34 beryllium kernel: [104497.073185]  [handle_mm_fault+0x118/0x730] handle_mm_fault+0x118/0x730
Apr  6 22:16:34 beryllium kernel: [104497.073205]  [apic_timer_interrupt+0x28/0x30] apic_timer_interrupt+0x28/0x30
Apr  6 22:16:34 beryllium kernel: [104497.073228]  [filemap_fault+0x29b/0x420] filemap_fault+0x29b/0x420
Apr  6 22:16:34 beryllium kernel: [104497.073240]  [do_page_fault+0x13f/0x730] do_page_fault+0x13f/0x730
Apr  6 22:16:34 beryllium kernel: [104497.073256]  [read_hpet+0xa/0x10] read_hpet+0xa/0x10
Apr  6 22:16:34 beryllium kernel: [104497.073259]  [snd_seq:do_gettimeofday+0x34/0xa540] do_gettimeofday+0x34/0xe0
Apr  6 22:16:34 beryllium kernel: [104497.073281]  [sys_gettimeofday+0x28/0x80] sys_gettimeofday+0x28/0x80
Apr  6 22:16:34 beryllium kernel: [104497.073292]  [do_page_fault+0x0/0x730] do_page_fault+0x0/0x730
Apr  6 22:16:34 beryllium kernel: [104497.073298]  [error_code+0x72/0x80] error_code+0x72/0x80
Apr  6 22:16:34 beryllium kernel: [104497.073339]  [unix_stream_recvmsg+0x3c0/0x550] unix_stream_recvmsg+0x3c0/0x550
Apr  6 22:16:34 beryllium kernel: [104497.073360]  =======================
Apr  6 22:16:34 beryllium kernel: [104497.073361] Mem-info:
Apr  6 22:16:34 beryllium kernel: [104497.073363] DMA per-cpu:
Apr  6 22:16:34 beryllium kernel: [104497.073366] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Apr  6 22:16:34 beryllium kernel: [104497.073368] CPU    1: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Apr  6 22:16:34 beryllium kernel: [104497.073371] Normal per-cpu:
Apr  6 22:16:34 beryllium kernel: [104497.073373] CPU    0: Hot: hi:  186, btch:  31 usd: 167   Cold: hi:   62, btch:  15 usd:  40
Apr  6 22:16:34 beryllium kernel: [104497.073376] CPU    1: Hot: hi:  186, btch:  31 usd: 149   Cold: hi:   62, btch:  15 usd:  50
Apr  6 22:16:34 beryllium kernel: [104497.073378] HighMem per-cpu:
Apr  6 22:16:34 beryllium kernel: [104497.073380] CPU    0: Hot: hi:   42, btch:   7 usd:  37   Cold: hi:   14, btch:   3 usd:   1
Apr  6 22:16:34 beryllium kernel: [104497.073383] CPU    1: Hot: hi:   42, btch:   7 usd:  38   Cold: hi:   14, btch:   3 usd:  11
Apr  6 22:16:34 beryllium kernel: [104497.073387] Active:212180 inactive:3862 dirty:0 writeback:0 unstable:0
Apr  6 22:16:34 beryllium kernel: [104497.073388]  free:2953 slab:3264 mapped:50 pagetables:878 bounce:0
Apr  6 22:16:34 beryllium kernel: [104497.073392] DMA free:4028kB min:68kB low:84kB high:100kB active:8220kB inactive:0kB present:16256kB pages_scanned:474677 all_unreclaimable? yes
Apr  6 22:16:34 beryllium kernel: [104497.073394] lowmem_reserve[]: 0 873 990 990
Apr  6 22:16:34 beryllium kernel: [104497.073399] Normal free:7500kB min:3744kB low:4680kB high:5616kB active:726144kB inactive:13212kB present:894080kB pages_scanned:2179863 all_unreclaimable? yes
Apr  6 22:16:34 beryllium kernel: [104497.073402] lowmem_reserve[]: 0 0 940 940
Apr  6 22:16:34 beryllium kernel: [104497.073407] HighMem free:284kB min:128kB low:252kB high:380kB active:114484kB inactive:2108kB present:120396kB pages_scanned:896 all_unreclaimable? no
Apr  6 22:16:34 beryllium kernel: [104497.073410] lowmem_reserve[]: 0 0 0 0
Apr  6 22:16:34 beryllium kernel: [104497.073413] DMA: 1*4kB 1*8kB 1*16kB 1*32kB 0*64kB 1*128kB 1*256kB 1*512kB 1*1024kB 1*2048kB 0*4096kB = 4028kB
Apr  6 22:16:34 beryllium kernel: [104497.073421] Normal: 885*4kB 1*8kB 1*16kB 1*32kB 1*64kB 0*128kB 1*256kB 1*512kB 1*1024kB 1*2048kB 0*4096kB = 7500kB
Apr  6 22:16:34 beryllium kernel: [104497.073429] HighMem: 45*4kB 0*8kB 2*16kB 0*32kB 1*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 276kB
Apr  6 22:16:34 beryllium kernel: [104497.073437] Swap cache: add 0, delete 0, find 0/0, race 0+0
Apr  6 22:16:34 beryllium kernel: [104497.073439] Free swap  = 0kB
Apr  6 22:16:34 beryllium kernel: [104497.073440] Total swap = 0kB
Apr  6 22:16:34 beryllium kernel: [104497.073442] Free swap:            0kB
Apr  6 22:16:34 beryllium kernel: [104497.078032] 259712 pages of RAM
Apr  6 22:16:34 beryllium kernel: [104497.078034] 30336 pages of HIGHMEM
Apr  6 22:16:34 beryllium kernel: [104497.078036] 3284 reserved pages
Apr  6 22:16:34 beryllium kernel: [104497.078038] 33516 pages shared
Apr  6 22:16:34 beryllium kernel: [104497.078039] 0 pages swap cached
Apr  6 22:16:34 beryllium kernel: [104497.078041] 0 pages dirty
Apr  6 22:16:34 beryllium kernel: [104497.078042] 0 pages writeback
Apr  6 22:16:34 beryllium kernel: [104497.078044] 50 pages mapped
Apr  6 22:16:34 beryllium kernel: [104497.078045] 3264 pages slab
Apr  6 22:16:34 beryllium kernel: [104497.078046] 878 pages pagetables
Apr  6 22:37:59 beryllium pulseaudio[21799]: pid.c: Stale PID file, overwriting.
Apr  6 23:00:26 beryllium -- MARK --

```

---

### Post by strider22 on 2009-04-07
Further checking indicates my swap partition is no longer configured???

fdisk shows this note on what I am sure used to be my swap;
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.

Is it safe to add the swap back into fstab? or does the note about boundary error indicate a problem?

would this be the correct entry?
/dev/sda1       none            swap    sw   pri=1           0       0

fdisk output. (sdb1 is a usb disk)
```

chris@beryllium:~$ sudo fdisk -l
sudo: unable to resolve host beryllium

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x970575bf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       13083   103550976    7  HPFS/NTFS
/dev/sda3           18591       19458     6962176   17  Hidden HPFS/NTFS
/dev/sda4           13084       18590    44234977+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    c  W95 FAT32 (LBA)

```

free output;
```

chris@beryllium:~$ free
             total       used       free     shared    buffers     cached
Mem:       1025716     980256      45460          0      39240     258076
-/+ buffers/cache:     682940     342776
Swap:            0          0          0

```

---

### Post by hyper_ch on 2009-04-07
(1) install "iotop" and let it run in a terminal... it shows you what process reads/writes to harddisks

(2) as for swap, /dev/sda1 is not being listed as swap drive. Are you sue it hsould be the swap one?

---

### Post by strider22 on 2009-04-07
The sda1 was a relic from the vista/tosiba original system.

Found it hard to believe ubuntu has been ok this long without a swap system.
To keep it easy I put in a swap file per these instructions;
[http://ubuntuforums.org/showthread.php?t=89782](http://ubuntuforums.org/showthread.php?t=89782)

Thanks for the help.

---

### Post by sdennie on 2009-04-07
It's hard to say.  The problem is that something ends up eating all your memory but I'm not sure what.  The hal segfaults are strange but, I have a feeling the problem is actually related to a failed suspend/resume.  Try turning off the "Suspend on Idle" functionality in System->Preferences->Power Management.

Edit:
Hmmm.  Actually, are you turning off your wifi with a physical switch at any time?

---

### Post by strider22 on 2009-04-07
re turning off the wifi... Yes it is turned off. Good catch.

---

### Post by sdennie on 2009-04-07
> **strider22 said:**
> re turning off the wifi... Yes it is turned off. Good catch.

In that case, try leaving the wifi switch turned on for a night and see if you have the same problem.  I would recommend turning it on and rebooting because, the logs make me think that it's the off state that is causing a problem and I don't know if turning it back on again will actually fix it unless you reboot.

---

### Post by Black Raven on 2009-05-16
It's definitely not related to neither wifi nor fdisk nor hal nor ny other software package. Seems that it's related only to kernel.

I had same issue on my Ubuntu Jaunty:
```
May 12 07:51:41 big -- MARK --
May 12 08:00:37 big kernel: [233387.108621] type=1503 audit(1242100837.141:10): operation="capable" name="sys_admin" pid=11357 profile="/usr/sbin/cupsd"
May 12 08:00:37 big kernel: [233387.108630] type=1503 audit(1242100837.141:11): operation="capable" name="sys_resource" pid=11357 profile="/usr/sbin/cupsd"
May 12 08:00:37 big kernel: [233387.108636] type=1503 audit(1242100837.141:12): operation="capable" name="sys_rawio" pid=11357 profile="/usr/sbin/cupsd"
May 12 08:00:37 big kernel: [233387.108652] type=1503 audit(1242100837.141:13): operation="capable" name="sys_admin" pid=11357 profile="/sbin/dhclient3"
May 12 08:00:37 big kernel: [233387.108657] type=1503 audit(1242100837.141:14): operation="capable" name="sys_resource" pid=11357 profile="/sbin/dhclient3"
May 12 08:00:37 big kernel: [233387.108663] type=1503 audit(1242100837.141:15): operation="capable" name="sys_rawio" pid=11357 profile="/sbin/dhclient3"
May 12 08:00:37 big kernel: [233387.108843] rhythmbox invoked oom-killer: gfp_mask=0x1201d2, order=0, oomkilladj=0
May 12 08:00:37 big kernel: [233387.108848] Pid: 11357, comm: rhythmbox Tainted: P           2.6.28-12-generic #43-Ubuntu
May 12 08:00:37 big kernel: [233387.108851] Call Trace:
May 12 08:00:37 big kernel: [233387.108862]  [<c04fca36>] ? printk+0x18/0x1a
May 12 08:00:37 big kernel: [233387.108868]  [<c0191525>] oom_kill_process+0x75/0x210
May 12 08:00:37 big kernel: [233387.108872]  [<c0191c03>] ? select_bad_process+0xc3/0x100
May 12 08:00:37 big kernel: [233387.108877]  [<c0191ce2>] out_of_memory+0xa2/0x140
May 12 08:00:37 big kernel: [233387.108881]  [<c0194350>] __alloc_pages_internal+0x450/0x490
May 12 08:00:37 big kernel: [233387.108886]  [<c0196c52>] __do_page_cache_readahead+0xd2/0x1d0
May 12 08:00:37 big kernel: [233387.108890]  [<c0196d9b>] do_page_cache_readahead+0x4b/0x70
May 12 08:00:37 big kernel: [233387.108894]  [<c018fd78>] filemap_fault+0x318/0x3e0
May 12 08:00:37 big kernel: [233387.108899]  [<c01a0f1b>] __do_fault+0x3b/0x470
May 12 08:00:37 big kernel: [233387.108904]  [<c04272fd>] ? skb_dequeue+0x4d/0x70
May 12 08:00:37 big kernel: [233387.108909]  [<c01a1e39>] handle_mm_fault+0x119/0x380
May 12 08:00:37 big kernel: [233387.108915]  [<c012ad96>] ? dequeue_entity+0x16/0x2a0
May 12 08:00:37 big kernel: [233387.108919]  [<c050118d>] do_page_fault+0x1fd/0x790
May 12 08:00:37 big kernel: [233387.108924]  [<c0102ab7>] ? __switch_to+0xb7/0x1a0
May 12 08:00:37 big kernel: [233387.108929]  [<c0122d58>] ? default_spin_lock_flags+0x8/0x10
May 12 08:00:37 big kernel: [233387.108934]  [<c04feb7e>] ? _spin_lock_irqsave+0x2e/0x40
May 12 08:00:37 big kernel: [233387.108939]  [<c0152a0a>] ? hrtimer_try_to_cancel+0x3a/0x90
May 12 08:00:37 big kernel: [233387.108943]  [<c0152a71>] ? hrtimer_cancel+0x11/0x20
May 12 08:00:37 big kernel: [233387.108947]  [<c04fded9>] ? do_nanosleep+0x99/0xc0
May 12 08:00:37 big kernel: [233387.108951]  [<c0153083>] ? hrtimer_nanosleep+0xf3/0x180
May 12 08:00:37 big kernel: [233387.108955]  [<c0152440>] ? hrtimer_wakeup+0x0/0x20
May 12 08:00:37 big kernel: [233387.108959]  [<c04fdebf>] ? do_nanosleep+0x7f/0xc0
May 12 08:00:37 big kernel: [233387.108963]  [<c0153170>] ? sys_nanosleep+0x60/0x70
May 12 08:00:37 big kernel: [233387.108966]  [<c0500f90>] ? do_page_fault+0x0/0x790
May 12 08:00:37 big kernel: [233387.108970]  [<c04feff2>] error_code+0x72/0x80
May 12 08:00:37 big kernel: [233387.108973] Mem-Info:
May 12 08:00:37 big kernel: [233387.108975] DMA per-cpu:
May 12 08:00:37 big kernel: [233387.108978] CPU    0: hi:    0, btch:   1 usd:   0
May 12 08:00:37 big kernel: [233387.108981] CPU    1: hi:    0, btch:   1 usd:   0
May 12 08:00:37 big kernel: [233387.108983] Normal per-cpu:
May 12 08:00:37 big kernel: [233387.108985] CPU    0: hi:  186, btch:  31 usd:  64
May 12 08:00:37 big kernel: [233387.108988] CPU    1: hi:  186, btch:  31 usd: 111
May 12 08:00:37 big kernel: [233387.108990] HighMem per-cpu:
May 12 08:00:37 big kernel: [233387.108992] CPU    0: hi:  186, btch:  31 usd:  55
May 12 08:00:37 big kernel: [233387.108995] CPU    1: hi:  186, btch:  31 usd:  61
May 12 08:00:37 big kernel: [233387.109000] Active_anon:308247 active_file:643 inactive_anon:164139
May 12 08:00:37 big kernel: [233387.109001]  inactive_file:3442 unevictable:2 dirty:4 writeback:0 unstable:0
May 12 08:00:37 big kernel: [233387.109002]  free:12464 slab:8574 mapped:6798 pagetables:1932 bounce:0
May 12 08:00:37 big kernel: [233387.109007] DMA free:8124kB min:64kB low:80kB high:96kB active_anon:256kB inactive_anon:324kB active_file:0kB inactive_file:4kB unevictable:0kB present:15804kB pages_scanned:916 all_unreclaimable? yes
May 12 08:00:37 big kernel: [233387.109011] lowmem_reserve[]: 0 861 2015 2015
May 12 08:00:37 big kernel: [233387.109020] Normal free:41256kB min:3720kB low:4648kB high:5580kB active_anon:368492kB inactive_anon:367992kB active_file:440kB inactive_file:1248kB unevictable:0kB present:881880kB pages_scanned:2177312 a
ll_unreclaimable? yes
May 12 08:00:37 big kernel: [233387.109023] lowmem_reserve[]: 0 0 9235 9235
May 12 08:00:37 big kernel: [233387.109032] HighMem free:476kB min:512kB low:1756kB high:3004kB active_anon:864240kB inactive_anon:288240kB active_file:2132kB inactive_file:12516kB unevictable:8kB present:1182120kB pages_scanned:1969056 
all_unreclaimable? yes
May 12 08:00:37 big kernel: [233387.109035] lowmem_reserve[]: 0 0 0 0
May 12 08:00:37 big kernel: [233387.109041] DMA: 5*4kB 5*8kB 6*16kB 5*32kB 6*64kB 6*128kB 6*256kB 6*512kB 2*1024kB 0*2048kB 0*4096kB = 8124kB
May 12 08:00:37 big kernel: [233387.109054] Normal: 1096*4kB 565*8kB 1692*16kB 45*32kB 8*64kB 4*128kB 3*256kB 0*512kB 0*1024kB 1*2048kB 0*4096kB = 41256kB
May 12 08:00:37 big kernel: [233387.109066] HighMem: 15*4kB 8*8kB 0*16kB 1*32kB 3*64kB 1*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 476kB
May 12 08:00:37 big kernel: [233387.109079] 4288 total pagecache pages
May 12 08:00:37 big kernel: [233387.109081] 1 pages in swap cache
May 12 08:00:37 big kernel: [233387.109084] Swap cache stats: add 1077658, delete 1077657, find 268689/329272
May 12 08:00:37 big kernel: [233387.109087] Free swap  = 0kB
May 12 08:00:37 big kernel: [233387.109089] Total swap = 2000052kB
May 12 08:00:37 big kernel: [233387.114904] 524144 pages RAM
May 12 08:00:37 big kernel: [233387.114907] 297858 pages HighMem
May 12 08:00:37 big kernel: [233387.114909] 8794 pages reserved
May 12 08:00:37 big kernel: [233387.114911] 14931 pages shared
May 12 08:00:37 big kernel: [233387.114913] 494101 pages non-shared
May 12 10:25:21 big syslogd 1.5.0#5ubuntu3: restart.

```

But I have no wifi at all :)
At one morning I found my system frozen. After reboot tI found this stuff in logs.

---

