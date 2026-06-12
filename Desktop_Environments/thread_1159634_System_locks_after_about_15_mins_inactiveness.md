---
title: "System locks after about 15 mins inactiveness"
date: 2009-05-14
forum: Desktop Environments
---

### Post by fornix on 2009-05-14
I am running Kubuntu 9.10 and have come across a strange problem. I have noticed that when I keep the PC idle for about 15-20 minutes, the black screen appears. Then i never get the control back. The monitor LED blinks. I have observed this only when I am in kde. Gnome works fine. 
My amarok and pidgin was running when this happened.
Here i am pasting the /var/log/messages of the time when this happened. This happened on May 14th around 12:11 pm.

```
May 14 12:10:58 nanosoft kernel: [ 6786.529595] type=1503 audit(1242283226.572:12): operation="capable" name="sys_admin" pid=7093 profile="/usr/sbin/cupsd"
May 14 12:11:05 nanosoft kernel: [ 6786.529603] type=1503 audit(1242283226.572:13): operation="capable" name="sys_resource" pid=7093 profile="/usr/sbin/cupsd"
May 14 12:11:10 nanosoft kernel: [ 6786.529608] type=1503 audit(1242283226.572:14): operation="capable" name="sys_rawio" pid=7093 profile="/usr/sbin/cupsd"
May 14 12:11:13 nanosoft kernel: [ 6786.529832] amarok invoked oom-killer: gfp_mask=0x1201d2, order=0, oomkilladj=0
May 14 12:11:15 nanosoft kernel: [ 6786.529837] Pid: 7093, comm: amarok Tainted: P           2.6.28-11-generic #42-Ubuntu
May 14 12:11:16 nanosoft kernel: [ 6786.529839] Call Trace:
May 14 12:11:17 nanosoft kernel: [ 6786.529849]  [<c0500ac6>] ? printk+0x18/0x1a
May 14 12:11:18 nanosoft kernel: [ 6786.529854]  [<c0191505>] oom_kill_process+0x75/0x210
May 14 12:11:27 nanosoft kernel: [ 6786.529857]  [<c0191be3>] ? select_bad_process+0xc3/0x100
May 14 12:11:28 nanosoft kernel: [ 6786.529860]  [<c0191cc2>] out_of_memory+0xa2/0x140
May 14 12:11:28 nanosoft kernel: [ 6786.529864]  [<c0194330>] __alloc_pages_internal+0x450/0x490
May 14 12:11:28 nanosoft kernel: [ 6786.529867]  [<c0196c32>] __do_page_cache_readahead+0xd2/0x1d0
May 14 12:11:28 nanosoft kernel: [ 6786.529871]  [<c0196d7b>] do_page_cache_readahead+0x4b/0x70
May 14 12:11:28 nanosoft kernel: [ 6786.529874]  [<c018fd58>] filemap_fault+0x318/0x3e0
May 14 12:11:28 nanosoft kernel: [ 6786.529878]  [<c01a0efb>] __do_fault+0x3b/0x470
May 14 12:11:28 nanosoft kernel: [ 6786.529882]  [<c01a1e19>] handle_mm_fault+0x119/0x380
May 14 12:11:28 nanosoft kernel: [ 6786.529887]  [<c0122d58>] ? default_spin_lock_flags+0x8/0x10
May 14 12:11:28 nanosoft kernel: [ 6786.529891]  [<c0502c0e>] ? _spin_lock_irqsave+0x2e/0x40
May 14 12:11:28 nanosoft kernel: [ 6786.529894]  [<c050521d>] do_page_fault+0x1fd/0x790
May 14 12:11:28 nanosoft kernel: [ 6786.529898]  [<c015dab6>] ? futex_wait+0x3c6/0x440
May 14 12:11:28 nanosoft kernel: [ 6786.529901]  [<c0152420>] ? hrtimer_wakeup+0x0/0x20
May 14 12:11:28 nanosoft kernel: [ 6786.529904]  [<c015d997>] ? futex_wait+0x2a7/0x440
May 14 12:11:28 nanosoft kernel: [ 6786.529907]  [<c0502cf8>] ? _spin_lock+0x8/0x10
May 14 12:11:28 nanosoft kernel: [ 6786.529909]  [<c015d4e8>] ? futex_wake+0xc8/0xf0
May 14 12:11:28 nanosoft kernel: [ 6786.529912]  [<c015e716>] ? do_futex+0x56/0x160
May 14 12:11:28 nanosoft kernel: [ 6786.529915]  [<c015e8b4>] ? sys_futex+0x94/0x110
May 14 12:11:28 nanosoft kernel: [ 6786.529918]  [<c0505020>] ? do_page_fault+0x0/0x790
May 14 12:11:28 nanosoft kernel: [ 6786.529921]  [<c0503082>] error_code+0x72/0x80
May 14 12:11:28 nanosoft kernel: [ 6786.529923] Mem-Info:
May 14 12:11:28 nanosoft kernel: [ 6786.529925] DMA per-cpu:
May 14 12:11:28 nanosoft kernel: [ 6786.529927] CPU    0: hi:    0, btch:   1 usd:   0
May 14 12:11:28 nanosoft kernel: [ 6786.529929] CPU    1: hi:    0, btch:   1 usd:   0
May 14 12:11:28 nanosoft kernel: [ 6786.529931] Normal per-cpu:
May 14 12:11:28 nanosoft kernel: [ 6786.529933] CPU    0: hi:  186, btch:  31 usd: 111
May 14 12:11:28 nanosoft kernel: [ 6786.529935] CPU    1: hi:  186, btch:  31 usd:  62
May 14 12:11:28 nanosoft kernel: [ 6786.529937] HighMem per-cpu:
May 14 12:11:28 nanosoft kernel: [ 6786.529939] CPU    0: hi:  186, btch:  31 usd: 164
May 14 12:11:28 nanosoft kernel: [ 6786.529941] CPU    1: hi:  186, btch:  31 usd: 178
May 14 12:11:28 nanosoft kernel: [ 6786.529945] Active_anon:211266 active_file:90 inactive_anon:211254
May 14 12:11:28 nanosoft kernel: [ 6786.529946]  inactive_file:183 unevictable:13 dirty:0 writeback:0 unstable:0
May 14 12:11:28 nanosoft kernel: [ 6786.529947]  free:10016 slab:4454 mapped:587 pagetables:1885 bounce:0
May 14 12:11:28 nanosoft kernel: [ 6786.529951] DMA free:7096kB min:64kB low:80kB high:96kB active_anon:732kB inactive_anon:900kB active_file:0kB inactive_file:0kB unevictable:0kB present:15804kB pages_scanned:3153 all_unreclaimable? yes
May 14 12:11:28 nanosoft kernel: [ 6786.529955] lowmem_reserve[]: 0 861 1761 1761
May 14 12:11:28 nanosoft kernel: [ 6786.529962] Normal free:32472kB min:3720kB low:4648kB high:5580kB active_anon:390188kB inactive_anon:389996kB active_file:356kB inactive_file:676kB unevictable:4kB present:881880kB pages_scanned:2249081 all_unreclaimable? yes
May 14 12:11:28 nanosoft kernel: [ 6786.529965] lowmem_reserve[]: 0 0 7198 7198
May 14 12:11:28 nanosoft kernel: [ 6786.529972] HighMem free:496kB min:512kB low:1484kB high:2456kB active_anon:454044kB inactive_anon:454120kB active_file:4kB inactive_file:56kB unevictable:48kB present:921456kB pages_scanned:11841157 all_unreclaimable? yes
May 14 12:11:28 nanosoft kernel: [ 6786.529975] lowmem_reserve[]: 0 0 0 0
May 14 12:11:28 nanosoft kernel: [ 6786.529979] DMA: 0*4kB 1*8kB 1*16kB 1*32kB 2*64kB 2*128kB 2*256kB 2*512kB 1*1024kB 2*2048kB 0*4096kB = 7096kB
May 14 12:11:28 nanosoft kernel: [ 6786.529988] Normal: 478*4kB 457*8kB 204*16kB 89*32kB 46*64kB 21*128kB 17*256kB 11*512kB 1*1024kB 0*2048kB 1*4096kB = 32416kB
May 14 12:11:28 nanosoft kernel: [ 6786.529997] HighMem: 4*4kB 12*8kB 2*16kB 1*32kB 1*64kB 0*128kB 1*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 496kB
May 14 12:11:28 nanosoft kernel: [ 6786.530006] 1847 total pagecache pages
May 14 12:11:28 nanosoft kernel: [ 6786.530008] 0 pages in swap cache
May 14 12:11:28 nanosoft kernel: [ 6786.530010] Swap cache stats: add 238251, delete 238251, find 5477/6027
May 14 12:11:28 nanosoft kernel: [ 6786.530012] Free swap  = 0kB
May 14 12:11:28 nanosoft kernel: [ 6786.530014] Total swap = 931728kB
May 14 12:11:28 nanosoft kernel: [ 6786.537706] 458464 pages RAM
May 14 12:11:28 nanosoft kernel: [ 6786.537709] 232178 pages HighMem
May 14 12:11:28 nanosoft kernel: [ 6786.537711] 7942 pages reserved
May 14 12:11:28 nanosoft kernel: [ 6786.537712] 3657 pages shared
May 14 12:11:28 nanosoft kernel: [ 6786.537714] 436254 pages non-shared
May 14 12:11:28 nanosoft kernel: [ 6796.937314] pidgin invoked oom-killer: gfp_mask=0x1201d2, order=0, oomkilladj=0
May 14 12:11:28 nanosoft kernel: [ 6796.937321] Pid: 7602, comm: pidgin Tainted: P           2.6.28-11-generic #42-Ubuntu
May 14 12:11:28 nanosoft kernel: [ 6796.937324] Call Trace:
May 14 12:11:28 nanosoft kernel: [ 6796.937334]  [<c0500ac6>] ? printk+0x18/0x1a
May 14 12:11:28 nanosoft kernel: [ 6796.937339]  [<c0191505>] oom_kill_process+0x75/0x210
May 14 12:11:28 nanosoft kernel: [ 6796.937342]  [<c0191be3>] ? select_bad_process+0xc3/0x100
May 14 12:11:28 nanosoft kernel: [ 6796.937345]  [<c0191cc2>] out_of_memory+0xa2/0x140
May 14 12:11:28 nanosoft kernel: [ 6796.937348]  [<c0194330>] __alloc_pages_internal+0x450/0x490
May 14 12:11:28 nanosoft kernel: [ 6796.937352]  [<c0196c32>] __do_page_cache_readahead+0xd2/0x1d0
May 14 12:11:28 nanosoft kernel: [ 6796.937356]  [<c0196d7b>] do_page_cache_readahead+0x4b/0x70
May 14 12:11:28 nanosoft kernel: [ 6796.937359]  [<c018fd58>] filemap_fault+0x318/0x3e0
May 14 12:11:28 nanosoft kernel: [ 6796.937362]  [<c01a0efb>] __do_fault+0x3b/0x470
May 14 12:11:28 nanosoft kernel: [ 6796.937366]  [<c038e259>] ? ata_sff_dma_pause+0x19/0x40
May 14 12:11:28 nanosoft kernel: [ 6796.937369]  [<c01a1e19>] handle_mm_fault+0x119/0x380
May 14 12:11:28 nanosoft kernel: [ 6796.937373]  [<c0105258>] ? invalidate_interrupt+0x28/0x30
May 14 12:11:28 nanosoft kernel: [ 6796.937377]  [<c050521d>] do_page_fault+0x1fd/0x790
May 14 12:11:28 nanosoft kernel: [ 6796.937380]  [<c0502cf8>] ? _spin_lock+0x8/0x10
May 14 12:11:28 nanosoft kernel: [ 6796.937384]  [<c011c7df>] ? ack_apic_level+0x6f/0x290
May 14 12:11:28 nanosoft kernel: [ 6796.937389]  [<c018049c>] ? handle_fasteoi_irq+0x8c/0xd0
May 14 12:11:28 nanosoft kernel: [ 6796.937393]  [<c0128ea0>] ? __wake_up_common+0x40/0x70
May 14 12:11:28 nanosoft kernel: [ 6796.937398]  [<c013f42f>] ? irq_exit+0x3f/0x90
May 14 12:11:28 nanosoft kernel: [ 6796.937401]  [<c0106853>] ? do_IRQ+0x83/0xa0
May 14 12:11:28 nanosoft kernel: [ 6796.937404]  [<c012a590>] ? __wake_up+0x40/0x50
May 14 12:11:28 nanosoft kernel: [ 6796.937407]  [<c01051f3>] ? common_interrupt+0x23/0x30
May 14 12:11:28 nanosoft kernel: [ 6796.937410]  [<c011fe8f>] ? read_hpet+0xf/0x20
May 14 12:11:28 nanosoft kernel: [ 6796.937415]  [<c01568f3>] ? getnstimeofday+0x53/0x110
May 14 12:11:28 nanosoft kernel: [ 6796.937420]  [<c01cb668>] ? poll_select_set_timeout+0x68/0x80
May 14 12:11:28 nanosoft kernel: [ 6796.937423]  [<c01cba54>] ? sys_poll+0x54/0xb0
May 14 12:11:28 nanosoft kernel: [ 6796.937426]  [<c0505020>] ? do_page_fault+0x0/0x790
May 14 12:11:28 nanosoft kernel: [ 6796.937429]  [<c0503082>] error_code+0x72/0x80
May 14 12:11:28 nanosoft kernel: [ 6796.937431] Mem-Info:
May 14 12:11:28 nanosoft kernel: [ 6796.937433] DMA per-cpu:
May 14 12:11:28 nanosoft kernel: [ 6796.937435] CPU    0: hi:    0, btch:   1 usd:   0
May 14 12:11:28 nanosoft kernel: [ 6796.937437] CPU    1: hi:    0, btch:   1 usd:   0
May 14 12:11:28 nanosoft kernel: [ 6796.937439] Normal per-cpu:
May 14 12:11:28 nanosoft kernel: [ 6796.937441] CPU    0: hi:  186, btch:  31 usd:  77
May 14 12:11:28 nanosoft kernel: [ 6796.937443] CPU    1: hi:  186, btch:  31 usd: 109
May 14 12:11:28 nanosoft kernel: [ 6796.937444] HighMem per-cpu:
May 14 12:11:28 nanosoft kernel: [ 6796.937446] CPU    0: hi:  186, btch:  31 usd: 165
May 14 12:11:28 nanosoft kernel: [ 6796.937448] CPU    1: hi:  186, btch:  31 usd: 167
May 14 12:11:28 nanosoft kernel: [ 6796.937452] Active_anon:211386 active_file:179 inactive_anon:211281
May 14 12:11:28 nanosoft kernel: [ 6796.937454]  inactive_file:425 unevictable:13 dirty:0 writeback:33 unstable:0
May 14 12:11:28 nanosoft kernel: [ 6796.937455]  free:10015 slab:4442 mapped:644 pagetables:1873 bounce:0
May 14 12:11:28 nanosoft kernel: [ 6796.937459] DMA free:7096kB min:64kB low:80kB high:96kB active_anon:732kB inactive_anon:900kB active_file:0kB inactive_file:0kB unevictable:0kB present:15804kB pages_scanned:3153 all_unreclaimable? yes
May 14 12:11:28 nanosoft kernel: [ 6796.937463] lowmem_reserve[]: 0 861 1761 1761
May 14 12:11:28 nanosoft kernel: [ 6796.937469] Normal free:32448kB min:3720kB low:4648kB high:5580kB active_anon:392592kB inactive_anon:392296kB active_file:544kB inactive_file:632kB unevictable:4kB present:881880kB pages_scanned:7054509 all_unreclaimable? yes
May 14 12:11:28 nanosoft kernel: [ 6796.937472] lowmem_reserve[]: 0 0 7198 7198
May 14 12:11:28 nanosoft kernel: [ 6796.937478] HighMem free:516kB min:512kB low:1484kB high:2456kB active_anon:452220kB inactive_anon:451928kB active_file:172kB inactive_file:1068kB unevictable:48kB present:921456kB pages_scanned:1504 all_unreclaimable? no
May 14 12:11:28 nanosoft kernel: [ 6796.937482] lowmem_reserve[]: 0 0 0 0
May 14 12:11:28 nanosoft kernel: [ 6796.937485] DMA: 0*4kB 1*8kB 1*16kB 1*32kB 2*64kB 2*128kB 2*256kB 2*512kB 1*1024kB 2*2048kB 0*4096kB = 7096kB
May 14 12:11:28 nanosoft kernel: [ 6796.937493] Normal: 478*4kB 457*8kB 204*16kB 90*32kB 46*64kB 21*128kB 17*256kB 11*512kB 1*1024kB 0*2048kB 1*4096kB = 32448kB
May 14 12:11:28 nanosoft kernel: [ 6796.937502] HighMem: 37*4kB 11*8kB 2*16kB 1*32kB 1*64kB 0*128kB 1*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 620kB
May 14 12:11:28 nanosoft kernel: [ 6796.937510] 2229 total pagecache pages
May 14 12:11:28 nanosoft kernel: [ 6796.937512] 22 pages in swap cache
May 14 12:11:28 nanosoft kernel: [ 6796.937514] Swap cache stats: add 238509, delete 238487, find 5477/6028
May 14 12:11:28 nanosoft kernel: [ 6796.937516] Free swap  = 0kB
May 14 12:11:28 nanosoft kernel: [ 6796.937517] Total swap = 931728kB
May 14 12:11:28 nanosoft kernel: [ 6796.945139] 458464 pages RAM
May 14 12:11:28 nanosoft kernel: [ 6796.945141] 232178 pages HighMem
May 14 12:11:28 nanosoft kernel: [ 6796.945143] 7942 pages reserved
May 14 12:11:28 nanosoft kernel: [ 6796.945144] 3373 pages shared
May 14 12:11:28 nanosoft kernel: [ 6796.945146] 436564 pages non-shared
May 14 12:11:28 nanosoft kernel: [ 6799.236312] kdesu invoked oom-killer: gfp_mask=0x1201d2, order=0, oomkilladj=0
May 14 12:11:28 nanosoft kernel: [ 6799.236319] Pid: 8692, comm: kdesu Tainted: P           2.6.28-11-generic #42-Ubuntu
May 14 12:11:28 nanosoft kernel: [ 6799.236321] Call Trace:
May 14 12:11:28 nanosoft kernel: [ 6799.236332]  [<c0500ac6>] ? printk+0x18/0x1a
May 14 12:11:28 nanosoft kernel: [ 6799.236337]  [<c0191505>] oom_kill_process+0x75/0x210
May 14 12:11:28 nanosoft kernel: [ 6799.236340]  [<c0191be3>] ? select_bad_process+0xc3/0x100
May 14 12:11:28 nanosoft kernel: [ 6799.236343]  [<c0191cc2>] out_of_memory+0xa2/0x140
May 14 12:11:28 nanosoft kernel: [ 6799.236346]  [<c0194330>] __alloc_pages_internal+0x450/0x490
May 14 12:11:28 nanosoft kernel: [ 6799.236350]  [<c0196c32>] __do_page_cache_readahead+0xd2/0x1d0
May 14 12:11:28 nanosoft kernel: [ 6799.236354]  [<c0196d7b>] do_page_cache_readahead+0x4b/0x70
May 14 12:11:28 nanosoft kernel: [ 6799.236357]  [<c018fd58>] filemap_fault+0x318/0x3e0
May 14 12:11:28 nanosoft kernel: [ 6799.236361]  [<c01a0efb>] __do_fault+0x3b/0x470
May 14 12:11:28 nanosoft kernel: [ 6799.236366]  [<c01227f6>] ? native_flush_tlb_single+0x6/0x10
May 14 12:11:28 nanosoft kernel: [ 6799.236369]  [<c01a1e19>] handle_mm_fault+0x119/0x380
May 14 12:11:28 nanosoft kernel: [ 6799.236373]  [<c050521d>] do_page_fault+0x1fd/0x790
May 14 12:11:28 nanosoft kernel: [ 6799.236378]  [<c01bd531>] ? do_sync_read+0xd1/0x110
May 14 12:11:28 nanosoft kernel: [ 6799.236384]  [<c028724f>] ? security_file_permission+0xf/0x20
May 14 12:11:28 nanosoft kernel: [ 6799.236388]  [<c014ecb0>] ? autoremove_wake_function+0x0/0x50
May 14 12:11:28 nanosoft kernel: [ 6799.236393]  [<c02a8ff9>] ? apparmor_file_permission+0x19/0x40
May 14 12:11:28 nanosoft kernel: [ 6799.236396]  [<c028724f>] ? security_file_permission+0xf/0x20
May 14 12:11:28 nanosoft kernel: [ 6799.236399]  [<c01bd5c4>] ? rw_verify_area+0x54/0xd0
May 14 12:11:28 nanosoft kernel: [ 6799.236402]  [<c01bdd1a>] ? vfs_read+0xfa/0x100
May 14 12:11:28 nanosoft kernel: [ 6799.236405]  [<c01bde07>] ? sys_read+0x67/0x70
May 14 12:11:28 nanosoft kernel: [ 6799.236408]  [<c0505020>] ? do_page_fault+0x0/0x790
May 14 12:11:28 nanosoft kernel: [ 6799.236411]  [<c0503082>] error_code+0x72/0x80
May 14 12:11:28 nanosoft kernel: [ 6799.236413] Mem-Info:
May 14 12:11:28 nanosoft kernel: [ 6799.236415] DMA per-cpu:
May 14 12:11:28 nanosoft kernel: [ 6799.236417] CPU    0: hi:    0, btch:   1 usd:   0
May 14 12:11:28 nanosoft kernel: [ 6799.236420] CPU    1: hi:    0, btch:   1 usd:   0
May 14 12:11:28 nanosoft kernel: [ 6799.236421] Normal per-cpu:
May 14 12:11:28 nanosoft kernel: [ 6799.236423] CPU    0: hi:  186, btch:  31 usd:  49
May 14 12:11:28 nanosoft kernel: [ 6799.236425] CPU    1: hi:  186, btch:  31 usd: 106
May 14 12:11:28 nanosoft kernel: [ 6799.236427] HighMem per-cpu:
May 14 12:11:28 nanosoft kernel: [ 6799.236429] CPU    0: hi:  186, btch:  31 usd:  80
May 14 12:11:28 nanosoft kernel: [ 6799.236431] CPU    1: hi:  186, btch:  31 usd: 124
May 14 12:11:28 nanosoft kernel: [ 6799.236435] Active_anon:211641 active_file:90 inactive_anon:211646
May 14 12:11:28 nanosoft kernel: [ 6799.236436]  inactive_file:744 unevictable:13 dirty:0 writeback:3485 unstable:0
May 14 12:11:28 nanosoft kernel: [ 6799.236438]  free:10074 slab:4522 mapped:622 pagetables:1846 bounce:0
May 14 12:11:28 nanosoft kernel: [ 6799.236442] DMA free:7096kB min:64kB low:80kB high:96kB active_anon:732kB inactive_anon:900kB active_file:0kB inactive_file:0kB unevictable:0kB present:15804kB pages_scanned:3153 all_unreclaimable? yes
May 14 12:11:28 nanosoft kernel: [ 6799.236445] lowmem_reserve[]: 0 861 1761 1761
May 14 12:11:28 nanosoft kernel: [ 6799.236452] Normal free:32500kB min:3720kB low:4648kB high:5580kB active_anon:393972kB inactive_anon:394100kB active_file:300kB inactive_file:744kB unevictable:4kB present:881880kB pages_scanned:88607 all_unreclaimable? no
May 14 12:11:28 nanosoft kernel: [ 6799.236455] lowmem_reserve[]: 0 0 7198 7198
May 14 12:11:28 nanosoft kernel: [ 6799.236461] HighMem free:700kB min:512kB low:1484kB high:2456kB active_anon:451860kB inactive_anon:451584kB active_file:60kB inactive_file:2232kB unevictable:48kB present:921456kB pages_scanned:66656 all_unreclaimable? no
May 14 12:11:28 nanosoft kernel: [ 6799.236464] lowmem_reserve[]: 0 0 0 0
May 14 12:11:28 nanosoft kernel: [ 6799.236468] DMA: 0*4kB 1*8kB 1*16kB 1*32kB 2*64kB 2*128kB 2*256kB 2*512kB 1*1024kB 2*2048kB 0*4096kB = 7096kB
May 14 12:11:28 nanosoft kernel: [ 6799.236476] Normal: 480*4kB 455*8kB 205*16kB 90*32kB 46*64kB 21*128kB 17*256kB 11*512kB 1*1024kB 0*2048kB 1*4096kB = 32456kB
May 14 12:11:28 nanosoft kernel: [ 6799.236485] HighMem: 80*4kB 7*8kB 1*16kB 1*32kB 1*64kB 0*128kB 1*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 744kB
May 14 12:11:28 nanosoft kernel: [ 6799.236493] 5879 total pagecache pages
May 14 12:11:28 nanosoft kernel: [ 6799.236495] 3503 pages in swap cache
May 14 12:11:28 nanosoft kernel: [ 6799.236497] Swap cache stats: add 242057, delete 238554, find 5477/6034
May 14 12:11:28 nanosoft kernel: [ 6799.236499] Free swap  = 0kB
May 14 12:11:28 nanosoft kernel: [ 6799.236500] Total swap = 931728kB
May 14 12:11:28 nanosoft kernel: [ 6799.244148] 458464 pages RAM
May 14 12:11:28 nanosoft kernel: [ 6799.244150] 232178 pages HighMem
May 14 12:11:28 nanosoft kernel: [ 6799.244151] 7942 pages reserved
May 14 12:11:28 nanosoft kernel: [ 6799.244153] 2575 pages shared
May 14 12:11:28 nanosoft kernel: [ 6799.244154] 437460 pages non-shared
May 14 12:11:28 nanosoft kernel: [ 6799.668563] pidgin invoked oom-killer: gfp_mask=0x1201d2, order=0, oomkilladj=0
May 14 12:11:28 nanosoft kernel: [ 6799.668570] Pid: 7545, comm: pidgin Tainted: P           2.6.28-11-generic #42-Ubuntu
May 14 12:11:28 nanosoft kernel: [ 6799.668573] Call Trace:
May 14 12:11:28 nanosoft kernel: [ 6799.668582]  [<c0500ac6>] ? printk+0x18/0x1a
May 14 12:11:28 nanosoft kernel: [ 6799.668587]  [<c0191505>] oom_kill_process+0x75/0x210
May 14 12:11:28 nanosoft kernel: [ 6799.668590]  [<c0191be3>] ? select_bad_process+0xc3/0x100
May 14 12:11:28 nanosoft kernel: [ 6799.668593]  [<c0191cc2>] out_of_memory+0xa2/0x140
May 14 12:11:28 nanosoft kernel: [ 6799.668596]  [<c0194330>] __alloc_pages_internal+0x450/0x490
May 14 12:11:28 nanosoft kernel: [ 6799.668600]  [<c0196c32>] __do_page_cache_readahead+0xd2/0x1d0
May 14 12:11:28 nanosoft kernel: [ 6799.668603]  [<c0196d7b>] do_page_cache_readahead+0x4b/0x70
May 14 12:11:28 nanosoft kernel: [ 6799.668606]  [<c018fd58>] filemap_fault+0x318/0x3e0
May 14 12:11:28 nanosoft kernel: [ 6799.668610]  [<c01a0efb>] __do_fault+0x3b/0x470
May 14 12:11:28 nanosoft kernel: [ 6799.668614]  [<c01a1e19>] handle_mm_fault+0x119/0x380
May 14 12:11:28 nanosoft kernel: [ 6799.668618]  [<c012c6fc>] ? enqueue_entity+0x13c/0x360
May 14 12:11:28 nanosoft kernel: [ 6799.668622]  [<c050521d>] do_page_fault+0x1fd/0x790
May 14 12:11:28 nanosoft kernel: [ 6799.668625]  [<c0133d0b>] ? default_wake_function+0xb/0x10
May 14 12:11:28 nanosoft kernel: [ 6799.668629]  [<c0128ea0>] ? __wake_up_common+0x40/0x70
May 14 12:11:28 nanosoft kernel: [ 6799.668632]  [<c012a590>] ? __wake_up+0x40/0x50
May 14 12:11:28 nanosoft kernel: [ 6799.668637]  [<c01568f3>] ? getnstimeofday+0x53/0x110
May 14 12:11:28 nanosoft kernel: [ 6799.668641]  [<c01cb668>] ? poll_select_set_timeout+0x68/0x80
May 14 12:11:28 nanosoft kernel: [ 6799.668644]  [<c01cba54>] ? sys_poll+0x54/0xb0
May 14 12:11:28 nanosoft kernel: [ 6799.668647]  [<c0505020>] ? do_page_fault+0x0/0x790
May 14 12:11:28 nanosoft kernel: [ 6799.668650]  [<c0503082>] error_code+0x72/0x80
May 14 12:11:28 nanosoft kernel: [ 6799.668652] Mem-Info:
May 14 12:11:28 nanosoft kernel: [ 6799.668654] DMA per-cpu:
May 14 12:11:28 nanosoft kernel: [ 6799.668656] CPU    0: hi:    0, btch:   1 usd:   0
May 14 12:11:28 nanosoft kernel: [ 6799.668658] CPU    1: hi:    0, btch:   1 usd:   0
May 14 12:11:28 nanosoft kernel: [ 6799.668660] Normal per-cpu:
May 14 12:11:28 nanosoft kernel: [ 6799.668662] CPU    0: hi:  186, btch:  31 usd:  50
May 14 12:11:28 nanosoft kernel: [ 6799.668664] CPU    1: hi:  186, btch:  31 usd:  48
May 14 12:11:28 nanosoft kernel: [ 6799.668665] HighMem per-cpu:
May 14 12:11:28 nanosoft kernel: [ 6799.668667] CPU    0: hi:  186, btch:  31 usd: 169
May 14 12:11:28 nanosoft kernel: [ 6799.668669] CPU    1: hi:  186, btch:  31 usd:  79
May 14 12:11:28 nanosoft kernel: [ 6799.668673] Active_anon:211672 active_file:66 inactive_anon:211699
May 14 12:11:28 nanosoft kernel: [ 6799.668674]  inactive_file:449 unevictable:13 dirty:0 writeback:3735 unstable:0
May 14 12:11:28 nanosoft kernel: [ 6799.668676]  free:10193 slab:4539 mapped:572 pagetables:1846 bounce:0
May 14 12:11:28 nanosoft kernel: [ 6799.668680] DMA free:7096kB min:64kB low:80kB high:96kB active_anon:732kB inactive_anon:900kB active_file:0kB inactive_file:0kB unevictable:0kB present:15804kB pages_scanned:3153 all_unreclaimable? yes
May 14 12:11:28 nanosoft kernel: [ 6799.668683] lowmem_reserve[]: 0 861 1761 1761
May 14 12:11:28 nanosoft kernel: [ 6799.668689] Normal free:32432kB min:3720kB low:4648kB high:5580kB active_anon:394604kB inactive_anon:394748kB active_file:240kB inactive_file:524kB unevictable:4kB present:881880kB pages_scanned:87961 all_unreclaimable? no
May 14 12:11:28 nanosoft kernel: [ 6799.668693] lowmem_reserve[]: 0 0 7198 7198
May 14 12:11:28 nanosoft kernel: [ 6799.668699] HighMem free:1244kB min:512kB low:1484kB high:2456kB active_anon:451252kB inactive_anon:451260kB active_file:24kB inactive_file:1272kB unevictable:48kB present:921456kB pages_scanned:672 all_unreclaimable? no
May 14 12:11:28 nanosoft kernel: [ 6799.668702] lowmem_reserve[]: 0 0 0 0
May 14 12:11:28 nanosoft kernel: [ 6799.668705] DMA: 0*4kB 1*8kB 1*16kB 1*32kB 2*64kB 2*128kB 2*256kB 2*512kB 1*1024kB 2*2048kB 0*4096kB = 7096kB
May 14 12:11:28 nanosoft kernel: [ 6799.668714] Normal: 478*4kB 456*8kB 205*16kB 90*32kB 46*64kB 21*128kB 17*256kB 11*512kB 1*1024kB 0*2048kB 1*4096kB = 32456kB
May 14 12:11:28 nanosoft kernel: [ 6799.668722] HighMem: 182*4kB 18*8kB 1*16kB 1*32kB 1*64kB 0*128kB 1*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 1240kB
May 14 12:11:28 nanosoft kernel: [ 6799.668730] 5854 total pagecache pages
May 14 12:11:28 nanosoft kernel: [ 6799.668732] 3760 pages in swap cache
May 14 12:11:28 nanosoft kernel: [ 6799.668734] Swap cache stats: add 242338, delete 238578, find 5477/6037
May 14 12:11:28 nanosoft kernel: [ 6799.668736] Free swap  = 0kB
May 14 12:11:28 nanosoft kernel: [ 6799.668737] Total swap = 931728kB
May 14 12:11:28 nanosoft kernel: [ 6799.676291] 458464 pages RAM
May 14 12:11:28 nanosoft kernel: [ 6799.676293] 232178 pages HighMem
May 14 12:11:28 nanosoft kernel: [ 6799.676295] 7942 pages reserved
May 14 12:11:28 nanosoft kernel: [ 6799.676296] 2422 pages shared
May 14 12:11:28 nanosoft kernel: [ 6799.676298] 437463 pages non-shared
May 14 12:11:28 nanosoft kernel: [ 6843.928315] hald-addon-stor invoked oom-killer: gfp_mask=0x1201d2, order=0, oomkilladj=0
May 14 12:11:28 nanosoft kernel: [ 6843.928322] Pid: 3618, comm: hald-addon-stor Tainted: P           2.6.28-11-generic #42-Ubuntu
May 14 12:11:28 nanosoft kernel: [ 6843.928324] Call Trace:
May 14 12:11:28 nanosoft kernel: [ 6843.928334]  [<c0500ac6>] ? printk+0x18/0x1a
May 14 12:11:28 nanosoft kernel: [ 6843.928339]  [<c0191505>] oom_kill_process+0x75/0x210
May 14 12:11:28 nanosoft kernel: [ 6843.928342]  [<c0191be3>] ? select_bad_process+0xc3/0x100
May 14 12:11:28 nanosoft kernel: [ 6843.928345]  [<c0191cc2>] out_of_memory+0xa2/0x140
May 14 12:11:28 nanosoft kernel: [ 6843.928349]  [<c0194330>] __alloc_pages_internal+0x450/0x490
May 14 12:11:28 nanosoft kernel: [ 6843.928352]  [<c0196c32>] __do_page_cache_readahead+0xd2/0x1d0
May 14 12:11:28 nanosoft kernel: [ 6843.928356]  [<c0196d7b>] do_page_cache_readahead+0x4b/0x70
May 14 12:11:28 nanosoft kernel: [ 6843.928359]  [<c018fd58>] filemap_fault+0x318/0x3e0
May 14 12:11:28 nanosoft kernel: [ 6843.928363]  [<c01a0efb>] __do_fault+0x3b/0x470
May 14 12:11:28 nanosoft kernel: [ 6843.928366]  [<c0190f2e>] ? mempool_free_slab+0xe/0x10
May 14 12:11:28 nanosoft kernel: [ 6843.928370]  [<c02b7bef>] ? __freed_request+0xaf/0x120
May 14 12:11:28 nanosoft kernel: [ 6843.928373]  [<c01a1e19>] handle_mm_fault+0x119/0x380
May 14 12:11:28 nanosoft kernel: [ 6843.928377]  [<c050521d>] do_page_fault+0x1fd/0x790
May 14 12:11:28 nanosoft kernel: [ 6843.928382]  [<c02c7290>] ? kobject_put+0x20/0x50
May 14 12:11:28 nanosoft kernel: [ 6843.928387]  [<c0376cba>] ? sr_block_ioctl+0x4a/0x90
May 14 12:11:28 nanosoft kernel: [ 6843.928390]  [<c02c7290>] ? kobject_put+0x20/0x50
May 14 12:11:28 nanosoft kernel: [ 6843.928393]  [<c01cf830>] ? iput+0x20/0x60
May 14 12:11:28 nanosoft kernel: [ 6843.928397]  [<c01e34c5>] ? __blkdev_put+0x65/0x160
May 14 12:11:28 nanosoft kernel: [ 6843.928400]  [<c01d387d>] ? mntput_no_expire+0x1d/0x120
May 14 12:11:28 nanosoft kernel: [ 6843.928405]  [<c01beaba>] ? __fput+0x14a/0x1c0
May 14 12:11:28 nanosoft kernel: [ 6843.928408]  [<c01beb4f>] ? fput+0x1f/0x30
May 14 12:11:28 nanosoft kernel: [ 6843.928411]  [<c01bb539>] ? filp_close+0x49/0x70
May 14 12:11:28 nanosoft kernel: [ 6843.928414]  [<c01bb5da>] ? sys_close+0x7a/0xc0
May 14 12:11:28 nanosoft kernel: [ 6843.928416]  [<c0505020>] ? do_page_fault+0x0/0x790
May 14 12:11:28 nanosoft kernel: [ 6843.928419]  [<c0503082>] error_code+0x72/0x80
May 14 12:11:28 nanosoft kernel: [ 6843.928422] Mem-Info:
May 14 12:11:28 nanosoft kernel: [ 6843.928424] DMA per-cpu:
May 14 12:11:28 nanosoft kernel: [ 6843.928426] CPU    0: hi:    0, btch:   1 usd:   0
May 14 12:11:28 nanosoft kernel: [ 6843.928428] CPU    1: hi:    0, btch:   1 usd:   0
May 14 12:11:28 nanosoft kernel: [ 6843.928430] Normal per-cpu:
May 14 12:11:28 nanosoft kernel: [ 6843.928432] CPU    0: hi:  186, btch:  31 usd: 180
May 14 12:11:28 nanosoft kernel: [ 6843.928434] CPU    1: hi:  186, btch:  31 usd: 145
May 14 12:11:28 nanosoft kernel: [ 6843.928435] HighMem per-cpu:
May 14 12:11:28 nanosoft kernel: [ 6843.928437] CPU    0: hi:  186, btch:  31 usd: 158
May 14 12:11:28 nanosoft kernel: [ 6843.928439] CPU    1: hi:  186, btch:  31 usd: 138
May 14 12:11:28 nanosoft kernel: [ 6843.928443] Active_anon:211770 active_file:69 inactive_anon:211717
May 14 12:11:28 nanosoft kernel: [ 6843.928444]  inactive_file:113 unevictable:13 dirty:0 writeback:0 unstable:0
May 14 12:11:28 nanosoft kernel: [ 6843.928446]  free:10022 slab:4460 mapped:584 pagetables:1831 bounce:0
May 14 12:11:28 nanosoft kernel: [ 6843.928450] DMA free:7096kB min:64kB low:80kB high:96kB active_anon:732kB inactive_anon:900kB active_file:0kB inactive_file:0kB unevictable:0kB present:15804kB pages_scanned:3153 all_unreclaimable? yes
May 14 12:11:28 nanosoft kernel: [ 6843.928453] lowmem_reserve[]: 0 861 1761 1761
May 14 12:11:28 nanosoft kernel: [ 6843.928460] Normal free:32412kB min:3720kB low:4648kB high:5580kB active_anon:393260kB inactive_anon:392932kB active_file:268kB inactive_file:4kB unevictable:4kB present:881880kB pages_scanned:893224 all_unreclaimable? no
May 14 12:11:28 nanosoft kernel: [ 6843.928463] lowmem_reserve[]: 0 0 7198 7198
May 14 12:11:28 nanosoft kernel: [ 6843.928469] HighMem free:580kB min:512kB low:1484kB high:2456kB active_anon:453088kB inactive_anon:452924kB active_file:8kB inactive_file:448kB unevictable:48kB present:921456kB pages_scanned:2880 all_unreclaimable? no
May 14 12:11:28 nanosoft kernel: [ 6843.928472] lowmem_reserve[]: 0 0 0 0
May 14 12:11:28 nanosoft kernel: [ 6843.928475] DMA: 0*4kB 1*8kB 1*16kB 1*32kB 2*64kB 2*128kB 2*256kB 2*512kB 1*1024kB 2*2048kB 0*4096kB = 7096kB
May 14 12:11:28 nanosoft kernel: [ 6843.928484] Normal: 515*4kB 433*8kB 214*16kB 87*32kB 46*64kB 21*128kB 17*256kB 11*512kB 1*1024kB 0*2048kB 1*4096kB = 32468kB
May 14 12:11:28 nanosoft kernel: [ 6843.928492] HighMem: 35*4kB 14*8kB 1*16kB 1*32kB 1*64kB 0*128kB 1*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 620kB
May 14 12:11:28 nanosoft kernel: [ 6843.928501] 1795 total pagecache pages
May 14 12:11:28 nanosoft kernel: [ 6843.928503] 0 pages in swap cache
May 14 12:11:28 nanosoft kernel: [ 6843.928505] Swap cache stats: add 242954, delete 242954, find 5500/6128
May 14 12:11:28 nanosoft kernel: [ 6843.928507] Free swap  = 0kB
May 14 12:11:28 nanosoft kernel: [ 6843.928508] Total swap = 931728kB
May 14 12:11:28 nanosoft kernel: [ 6843.936285] 458464 pages RAM
May 14 12:11:28 nanosoft kernel: [ 6843.936287] 232178 pages HighMem
May 14 12:11:28 nanosoft kernel: [ 6843.936289] 7942 pages reserved
May 14 12:11:28 nanosoft kernel: [ 6843.936290] 2653 pages shared
May 14 12:11:28 nanosoft kernel: [ 6843.936291] 437084 pages non-shared
May 14 12:11:28 nanosoft kernel: [ 6848.111036] plasma invoked oom-killer: gfp_mask=0x1201d2, order=0, oomkilladj=0
May 14 12:11:28 nanosoft kernel: [ 6848.111042] Pid: 4346, comm: plasma Tainted: P           2.6.28-11-generic #42-Ubuntu
May 14 12:11:28 nanosoft kernel: [ 6848.111045] Call Trace:
May 14 12:11:28 nanosoft kernel: [ 6848.111054]  [<c0500ac6>] ? printk+0x18/0x1a
May 14 12:11:28 nanosoft kernel: [ 6848.111059]  [<c0191505>] oom_kill_process+0x75/0x210
May 14 12:11:28 nanosoft kernel: [ 6848.111062]  [<c0191be3>] ? select_bad_process+0xc3/0x100
May 14 12:11:28 nanosoft kernel: [ 6848.111065]  [<c0191cc2>] out_of_memory+0xa2/0x140
May 14 12:11:28 nanosoft kernel: [ 6848.111068]  [<c0194330>] __alloc_pages_internal+0x450/0x490
May 14 12:11:28 nanosoft kernel: [ 6848.111072]  [<c0196c32>] __do_page_cache_readahead+0xd2/0x1d0
May 14 12:11:28 nanosoft kernel: [ 6848.111076]  [<c0196d7b>] do_page_cache_readahead+0x4b/0x70
May 14 12:11:28 nanosoft kernel: [ 6848.111079]  [<c018fd58>] filemap_fault+0x318/0x3e0
May 14 12:11:28 nanosoft kernel: [ 6848.111083]  [<c01a0efb>] __do_fault+0x3b/0x470
May 14 12:11:28 nanosoft kernel: [ 6848.111086]  [<c01a1e19>] handle_mm_fault+0x119/0x380
May 14 12:11:28 nanosoft kernel: [ 6848.111090]  [<c02ccacc>] ? __const_udelay+0x2c/0x30
May 14 12:11:28 nanosoft kernel: [ 6848.111093]  [<c038e452>] ? ata_sff_pause+0x12/0x20
May 14 12:11:28 nanosoft kernel: [ 6848.111097]  [<c050521d>] do_page_fault+0x1fd/0x790
May 14 12:11:28 nanosoft kernel: [ 6848.111101]  [<c0151b1a>] ? hrtimer_forward+0x12a/0x170
May 14 12:11:28 nanosoft kernel: [ 6848.111105]  [<c01568f3>] ? getnstimeofday+0x53/0x110
May 14 12:11:28 nanosoft kernel: [ 6848.111109]  [<c0119a73>] ? lapic_next_event+0x13/0x20
May 14 12:11:28 nanosoft kernel: [ 6848.111113]  [<c0159b1a>] ? clockevents_program_event+0x9a/0x150
May 14 12:11:28 nanosoft kernel: [ 6848.111117]  [<c02ca49d>] ? rb_erase+0xcd/0x150
May 14 12:11:28 nanosoft kernel: [ 6848.111120]  [<c0102ab7>] ? __switch_to+0xb7/0x1a0
May 14 12:11:28 nanosoft kernel: [ 6848.111125]  [<c012f9cb>] ? finish_task_switch+0x2b/0xe0
May 14 12:11:28 nanosoft kernel: [ 6848.111128]  [<c01568f3>] ? getnstimeofday+0x53/0x110
May 14 12:11:28 nanosoft kernel: [ 6848.111133]  [<c01cb668>] ? poll_select_set_timeout+0x68/0x80
May 14 12:11:28 nanosoft kernel: [ 6848.111136]  [<c01cba54>] ? sys_poll+0x54/0xb0
May 14 12:11:28 nanosoft kernel: [ 6848.111139]  [<c0505020>] ? do_page_fault+0x0/0x790
May 14 12:11:28 nanosoft kernel: [ 6848.111142]  [<c0503082>] error_code+0x72/0x80
May 14 12:11:28 nanosoft kernel: [ 6848.111144] Mem-Info:
May 14 12:11:28 nanosoft kernel: [ 6848.111146] DMA per-cpu:
May 14 12:11:28 nanosoft kernel: [ 6848.111149] CPU    0: hi:    0, btch:   1 usd:   0
May 14 12:11:28 nanosoft kernel: [ 6848.111151] CPU    1: hi:    0, btch:   1 usd:   0
May 14 12:11:28 nanosoft kernel: [ 6848.111152] Normal per-cpu:
May 14 12:11:28 nanosoft kernel: [ 6848.111154] CPU    0: hi:  186, btch:  31 usd: 170
May 14 12:11:28 nanosoft kernel: [ 6848.111156] CPU    1: hi:  186, btch:  31 usd:  90
May 14 12:11:28 nanosoft kernel: [ 6848.111158] HighMem per-cpu:
May 14 12:11:28 nanosoft kernel: [ 6848.111160] CPU    0: hi:  186, btch:  31 usd: 113
May 14 12:11:28 nanosoft kernel: [ 6848.111162] CPU    1: hi:  186, btch:  31 usd:  50
May 14 12:11:28 nanosoft kernel: [ 6848.111166] Active_anon:211539 active_file:304 inactive_anon:211592
May 14 12:11:28 nanosoft kernel: [ 6848.111167]  inactive_file:1129 unevictable:13 dirty:0 writeback:1731 unstable:0
May 14 12:11:28 nanosoft kernel: [ 6848.111168]  free:10039 slab:4520 mapped:964 pagetables:1806 bounce:0
May 14 12:11:28 nanosoft kernel: [ 6848.111172] DMA free:7096kB min:64kB low:80kB high:96kB active_anon:732kB inactive_anon:900kB active_file:0kB inactive_file:0kB unevictable:0kB present:15804kB pages_scanned:3153 all_unreclaimable? yes
May 14 12:11:28 nanosoft kernel: [ 6848.111176] lowmem_reserve[]: 0 861 1761 1761
May 14 12:11:28 nanosoft kernel: [ 6848.111182] Normal free:32344kB min:3720kB low:4648kB high:5580kB active_anon:394960kB inactive_anon:395184kB active_file:336kB inactive_file:284kB unevictable:4kB present:881880kB pages_scanned:2185578 all_unreclaimable? yes
May 14 12:11:28 nanosoft kernel: [ 6848.111186] lowmem_reserve[]: 0 0 7198 7198
May 14 12:11:28 nanosoft kernel: [ 6848.111191] HighMem free:716kB min:512kB low:1484kB high:2456kB active_anon:450464kB inactive_anon:450284kB active_file:880kB inactive_file:4232kB unevictable:48kB present:921456kB pages_scanned:97828 all_unreclaimable? no
May 14 12:11:28 nanosoft kernel: [ 6848.111195] lowmem_reserve[]: 0 0 0 0
May 14 12:11:28 nanosoft kernel: [ 6848.111198] DMA: 0*4kB 1*8kB 1*16kB 1*32kB 2*64kB 2*128kB 2*256kB 2*512kB 1*1024kB 2*2048kB 0*4096kB = 7096kB
May 14 12:11:28 nanosoft kernel: [ 6848.111207] Normal: 484*4kB 433*8kB 214*16kB 87*32kB 46*64kB 21*128kB 17*256kB 11*512kB 1*1024kB 0*2048kB 1*4096kB = 32344kB
May 14 12:11:28 nanosoft kernel: [ 6848.111215] HighMem: 92*4kB 1*8kB 1*16kB 1*32kB 1*64kB 0*128kB 1*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 744kB
May 14 12:11:28 nanosoft kernel: [ 6848.111223] 4719 total pagecache pages
May 14 12:11:28 nanosoft kernel: [ 6848.111225] 1735 pages in swap cache
May 14 12:11:28 nanosoft kernel: [ 6848.111227] Swap cache stats: add 245633, delete 243898, find 5510/6146
May 14 12:11:28 nanosoft kernel: [ 6848.111229] Free swap  = 0kB
May 14 12:11:28 nanosoft kernel: [ 6848.111230] Total swap = 931728kB
May 14 12:11:28 nanosoft kernel: [ 6848.119072] 458464 pages RAM
May 14 12:11:28 nanosoft kernel: [ 6848.119075] 232178 pages HighMem
May 14 12:11:28 nanosoft kernel: [ 6848.119076] 7942 pages reserved
May 14 12:11:28 nanosoft kernel: [ 6848.119078] 2757 pages shared
May 14 12:11:28 nanosoft kernel: [ 6848.119079] 437493 pages non-shared
May 14 12:11:38 nanosoft pppd[4468]: Modem hangup
May 14 12:11:39 nanosoft pppd[4468]: Connect time 112.7 minutes.
May 14 12:11:39 nanosoft pppd[4468]: Sent 1662202 bytes, received 21333500 bytes.
May 14 12:11:50 nanosoft pppd[4468]: Connection terminated.
May 14 12:12:15 nanosoft pppd[4468]: Exit.
May 14 12:19:19 nanosoft kernel: [ 7312.588300] pidgin invoked oom-killer: gfp_mask=0x1201d2, order=0, oomkilladj=0
May 14 12:19:22 nanosoft kernel: [ 7312.588307] Pid: 8039, comm: pidgin Tainted: P           2.6.28-11-generic #42-Ubuntu
May 14 12:19:22 nanosoft kernel: [ 7312.588310] Call Trace:
May 14 12:19:22 nanosoft kernel: [ 7312.588321]  [<c0500ac6>] ? printk+0x18/0x1a
May 14 12:19:22 nanosoft kernel: [ 7312.588326]  [<c0191505>] oom_kill_process+0x75/0x210
May 14 12:19:22 nanosoft kernel: [ 7312.588329]  [<c0191be3>] ? select_bad_process+0xc3/0x100
May 14 12:19:22 nanosoft kernel: [ 7312.588332]  [<c0191cc2>] out_of_memory+0xa2/0x140
May 14 12:19:22 nanosoft kernel: [ 7312.588335]  [<c0194330>] __alloc_pages_internal+0x450/0x490
May 14 12:19:22 nanosoft kernel: [ 7312.588339]  [<c0196c32>] __do_page_cache_readahead+0xd2/0x1d0
May 14 12:19:22 nanosoft kernel: [ 7312.588342]  [<c0196d7b>] do_page_cache_readahead+0x4b/0x70
May 14 12:19:22 nanosoft kernel: [ 7312.588345]  [<c018fd58>] filemap_fault+0x318/0x3e0
May 14 12:19:22 nanosoft kernel: [ 7312.588349]  [<c01a0efb>] __do_fault+0x3b/0x470
May 14 12:19:22 nanosoft kernel: [ 7312.588353]  [<c01a1e19>] handle_mm_fault+0x119/0x380
May 14 12:19:22 nanosoft kernel: [ 7312.588355]  [<c050104a>] ? schedule+0x41a/0x710
May 14 12:19:22 nanosoft kernel: [ 7312.588359]  [<c050521d>] do_page_fault+0x1fd/0x790
May 14 12:19:22 nanosoft kernel: [ 7312.588363]  [<c015da48>] ? futex_wait+0x358/0x440
May 14 12:19:22 nanosoft kernel: [ 7312.588366]  [<c015ebe2>] ? rt_mutex_adjust_prio+0x32/0x50
May 14 12:19:22 nanosoft kernel: [ 7312.588369]  [<c050238d>] ? rt_mutex_slowunlock+0x2d/0x50
May 14 12:19:22 nanosoft kernel: [ 7312.588371]  [<c05023d4>] ? rt_mutex_unlock+0x24/0x30
May 14 12:19:22 nanosoft kernel: [ 7312.588374]  [<c015caae>] ? wake_futex_pi+0xde/0x1b0
May 14 12:19:22 nanosoft kernel: [ 7312.588377]  [<c0502cf8>] ? _spin_lock+0x8/0x10
May 14 12:19:22 nanosoft kernel: [ 7312.588379]  [<c015dd77>] ? futex_unlock_pi+0x1e7/0x2c0
May 14 12:19:22 nanosoft kernel: [ 7312.588384]  [<c01568f3>] ? getnstimeofday+0x53/0x110
May 14 12:19:22 nanosoft kernel: [ 7312.588387]  [<c01568f3>] ? getnstimeofday+0x53/0x110
May 14 12:19:22 nanosoft kernel: [ 7312.588391]  [<c02cd596>] ? copy_to_user+0x36/0x120
May 14 12:19:22 nanosoft kernel: [ 7312.588396]  [<c013ea4b>] ? sys_gettimeofday+0x2b/0x70
May 14 12:19:22 nanosoft kernel: [ 7312.588399]  [<c0505020>] ? do_page_fault+0x0/0x790
May 14 12:19:22 nanosoft kernel: [ 7312.588401]  [<c0503082>] error_code+0x72/0x80
May 14 12:19:22 nanosoft kernel: [ 7312.588404] Mem-Info:
May 14 12:19:22 nanosoft kernel: [ 7312.588406] DMA per-cpu:
May 14 12:19:22 nanosoft kernel: [ 7312.588408] CPU    0: hi:    0, btch:   1 usd:   0
May 14 12:19:22 nanosoft kernel: [ 7312.588410] CPU    1: hi:    0, btch:   1 usd:   0
May 14 12:19:22 nanosoft kernel: [ 7312.588412] Normal per-cpu:
May 14 12:19:22 nanosoft kernel: [ 7312.588414] CPU    0: hi:  186, btch:  31 usd: 179
May 14 12:19:22 nanosoft kernel: [ 7312.588416] CPU    1: hi:  186, btch:  31 usd: 100
May 14 12:19:22 nanosoft kernel: [ 7312.588417] HighMem per-cpu:
May 14 12:19:22 nanosoft kernel: [ 7312.588419] CPU    0: hi:  186, btch:  31 usd: 162
May 14 12:19:22 nanosoft kernel: [ 7312.588421] CPU    1: hi:  186, btch:  31 usd: 179
May 14 12:19:22 nanosoft kernel: [ 7312.588425] Active_anon:211590 active_file:77 inactive_anon:211252
May 14 12:19:22 nanosoft kernel: [ 7312.588426]  inactive_file:28 unevictable:13 dirty:0 writeback:0 unstable:0
May 14 12:19:22 nanosoft kernel: [ 7312.588427]  free:9999 slab:4551 mapped:589 pagetables:1791 bounce:0
May 14 12:19:22 nanosoft kernel: [ 7312.588432] DMA free:7096kB min:64kB low:80kB high:96kB active_anon:732kB inactive_anon:900kB active_file:0kB inactive_file:0kB unevictable:0kB present:15804kB pages_scanned:3153 all_unreclaimable? yes
May 14 12:19:22 nanosoft kernel: [ 7312.588435] lowmem_reserve[]: 0 861 1761 1761
May 14 12:19:22 nanosoft kernel: [ 7312.588441] Normal free:32404kB min:3720kB low:4648kB high:5580kB active_anon:393728kB inactive_anon:392536kB active_file:308kB inactive_file:44kB unevictable:4kB present:881880kB pages_scanned:2702813 all_unreclaimable? yes
May 14 12:19:22 nanosoft kernel: [ 7312.588445] lowmem_reserve[]: 0 0 7198 7198
May 14 12:19:22 nanosoft kernel: [ 7312.588451] HighMem free:496kB min:512kB low:1484kB high:2456kB active_anon:451800kB inactive_anon:451572kB active_file:0kB inactive_file:68kB unevictable:48kB present:921456kB pages_scanned:3828055 all_unreclaimable? no
May 14 12:19:22 nanosoft kernel: [ 7312.588454] lowmem_reserve[]: 0 0 0 0
May 14 12:19:22 nanosoft kernel: [ 7312.588458] DMA: 0*4kB 1*8kB 1*16kB 1*32kB 2*64kB 2*128kB 2*256kB 2*512kB 1*1024kB 2*2048kB 0*4096kB = 7096kB
May 14 12:19:22 nanosoft kernel: [ 7312.588466] Normal: 539*4kB 411*8kB 209*16kB 90*32kB 46*64kB 21*128kB 17*256kB 11*512kB 1*1024kB 0*2048kB 1*4096kB = 32404kB
May 14 12:19:22 nanosoft kernel: [ 7312.588475] HighMem: 32*4kB 0*8kB 1*16kB 1*32kB 1*64kB 0*128kB 1*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 496kB
May 14 12:19:22 nanosoft kernel: [ 7312.588483] 1664 total pagecache pages
May 14 12:19:22 nanosoft kernel: [ 7312.588485] 0 pages in swap cache
May 14 12:19:22 nanosoft kernel: [ 7312.588487] Swap cache stats: add 261911, delete 261911, find 6582/8506
May 14 12:19:22 nanosoft kernel: [ 7312.588489] Free swap  = 0kB
May 14 12:19:22 nanosoft kernel: [ 7312.588490] Total swap = 931728kB
May 14 12:19:22 nanosoft kernel: [ 7312.596307] 458464 pages RAM
May 14 12:19:22 nanosoft kernel: [ 7312.596310] 232178 pages HighMem
May 14 12:19:22 nanosoft kernel: [ 7312.596311] 7942 pages reserved
May 14 12:19:22 nanosoft kernel: [ 7312.596313] 3551 pages shared
May 14 12:19:22 nanosoft kernel: [ 7312.596314] 436245 pages non-shared
May 14 12:19:22 nanosoft kernel: [ 7315.873506] wineserver invoked oom-killer: gfp_mask=0x1201d2, order=0, oomkilladj=0
May 14 12:19:22 nanosoft kernel: [ 7315.873513] Pid: 7644, comm: wineserver Tainted: P           2.6.28-11-generic #42-Ubuntu
May 14 12:19:22 nanosoft kernel: [ 7315.873516] Call Trace:
May 14 12:19:22 nanosoft kernel: [ 7315.873526]  [<c0500ac6>] ? printk+0x18/0x1a
May 14 12:19:22 nanosoft kernel: [ 7315.873530]  [<c0191505>] oom_kill_process+0x75/0x210
May 14 12:19:22 nanosoft kernel: [ 7315.873533]  [<c0191be3>] ? select_bad_process+0xc3/0x100
May 14 12:19:22 nanosoft kernel: [ 7315.873536]  [<c0191cc2>] out_of_memory+0xa2/0x140
May 14 12:19:22 nanosoft kernel: [ 7315.873540]  [<c0194330>] __alloc_pages_internal+0x450/0x490
May 14 12:19:22 nanosoft kernel: [ 7315.873543]  [<c0196c32>] __do_page_cache_readahead+0xd2/0x1d0
May 14 12:19:22 nanosoft kernel: [ 7315.873547]  [<c0196d7b>] do_page_cache_readahead+0x4b/0x70
May 14 12:19:22 nanosoft kernel: [ 7315.873550]  [<c018fd58>] filemap_fault+0x318/0x3e0
May 14 12:19:22 nanosoft kernel: [ 7315.873554]  [<c01a0efb>] __do_fault+0x3b/0x470
May 14 12:19:22 nanosoft kernel: [ 7315.873558]  [<c01fe902>] ? tid_fd_revalidate+0x82/0x140
May 14 12:19:22 nanosoft kernel: [ 7315.873562]  [<c0127453>] ? kmap_atomic_prot+0x43/0xe0
May 14 12:19:22 nanosoft kernel: [ 7315.873565]  [<c01a1e19>] handle_mm_fault+0x119/0x380
May 14 12:19:22 nanosoft kernel: [ 7315.873570]  [<c050521d>] do_page_fault+0x1fd/0x790
May 14 12:19:22 nanosoft kernel: [ 7315.873574]  [<c011c7df>] ? ack_apic_level+0x6f/0x290
May 14 12:19:22 nanosoft kernel: [ 7315.873579]  [<c013f42f>] ? irq_exit+0x3f/0x90
May 14 12:19:22 nanosoft kernel: [ 7315.873583]  [<c0106853>] ? do_IRQ+0x83/0xa0
May 14 12:19:22 nanosoft kernel: [ 7315.873586]  [<c01d387d>] ? mntput_no_expire+0x1d/0x120
May 14 12:19:22 nanosoft kernel: [ 7315.873589]  [<c01051f3>] ? common_interrupt+0x23/0x30
May 14 12:19:22 nanosoft kernel: [ 7315.873593]  [<c01c5d65>] ? putname+0x25/0x40
May 14 12:19:22 nanosoft kernel: [ 7315.873596]  [<c01c5d65>] ? putname+0x25/0x40
May 14 12:19:22 nanosoft kernel: [ 7315.873599]  [<c01c8ae3>] ? user_path_at+0x53/0x80
May 14 12:19:22 nanosoft kernel: [ 7315.873601]  [<c0102ab7>] ? __switch_to+0xb7/0x1a0
May 14 12:19:22 nanosoft kernel: [ 7315.873604]  [<c01d387d>] ? mntput_no_expire+0x1d/0x120
May 14 12:19:22 nanosoft kernel: [ 7315.873607]  [<c01c5f20>] ? path_put+0x20/0x30
May 14 12:19:22 nanosoft kernel: [ 7315.873611]  [<c01e92bf>] ? sys_inotify_add_watch+0xcf/0x150
May 14 12:19:22 nanosoft kernel: [ 7315.873615]  [<c01bdddd>] ? sys_read+0x3d/0x70
May 14 12:19:22 nanosoft kernel: [ 7315.873618]  [<c0505020>] ? do_page_fault+0x0/0x790
May 14 12:19:22 nanosoft kernel: [ 7315.873621]  [<c0503082>] error_code+0x72/0x80
May 14 12:19:22 nanosoft kernel: [ 7315.873623] Mem-Info:
May 14 12:19:22 nanosoft kernel: [ 7315.873625] DMA per-cpu:
May 14 12:19:22 nanosoft kernel: [ 7315.873627] CPU    0: hi:    0, btch:   1 usd:   0
May 14 12:19:22 nanosoft kernel: [ 7315.873629] CPU    1: hi:    0, btch:   1 usd:   0
May 14 12:19:22 nanosoft kernel: [ 7315.873631] Normal per-cpu:
May 14 12:19:22 nanosoft kernel: [ 7315.873633] CPU    0: hi:  186, btch:  31 usd: 172
May 14 12:19:22 nanosoft kernel: [ 7315.873635] CPU    1: hi:  186, btch:  31 usd:  83
May 14 12:19:22 nanosoft kernel: [ 7315.873637] HighMem per-cpu:
May 14 12:19:22 nanosoft kernel: [ 7315.873639] CPU    0: hi:  186, btch:  31 usd: 101
May 14 12:19:22 nanosoft kernel: [ 7315.873641] CPU    1: hi:  186, btch:  31 usd: 139
May 14 12:19:22 nanosoft kernel: [ 7315.873645] Active_anon:211636 active_file:420 inactive_anon:211628
May 14 12:19:22 nanosoft kernel: [ 7315.873646]  inactive_file:1202 unevictable:13 dirty:0 writeback:0 unstable:0
May 14 12:19:22 nanosoft kernel: [ 7315.873647]  free:10016 slab:4555 mapped:1067 pagetables:1772 bounce:0
May 14 12:19:22 nanosoft kernel: [ 7315.873651] DMA free:7096kB min:64kB low:80kB high:96kB active_anon:732kB inactive_anon:900kB active_file:0kB inactive_file:0kB unevictable:0kB present:15804kB pages_scanned:3153 all_unreclaimable? yes
May 14 12:19:22 nanosoft kernel: [ 7315.873655] lowmem_reserve[]: 0 861 1761 1761
May 14 12:19:22 nanosoft kernel: [ 7315.873661] Normal free:32272kB min:3720kB low:4648kB high:5580kB active_anon:393960kB inactive_anon:393700kB active_file:524kB inactive_file:156kB unevictable:4kB present:881880kB pages_scanned:4998682 all_unreclaimable? yes
May 14 12:19:22 nanosoft kernel: [ 7315.873665] lowmem_reserve[]: 0 0 7198 7198
May 14 12:19:22 nanosoft kernel: [ 7315.873671] HighMem free:696kB min:512kB low:1484kB high:2456kB active_anon:451852kB inactive_anon:451912kB active_file:1156kB inactive_file:4652kB unevictable:48kB present:921456kB pages_scanned:20832 all_unreclaimable? no
May 14 12:19:22 nanosoft kernel: [ 7315.873674] lowmem_reserve[]: 0 0 0 0
May 14 12:19:22 nanosoft kernel: [ 7315.873677] DMA: 0*4kB 1*8kB 1*16kB 1*32kB 2*64kB 2*128kB 2*256kB 2*512kB 1*1024kB 2*2048kB 0*4096kB = 7096kB
May 14 12:19:22 nanosoft kernel: [ 7315.873686] Normal: 508*4kB 410*8kB 209*16kB 90*32kB 46*64kB 21*128kB 17*256kB 11*512kB 1*1024kB 0*2048kB 1*4096kB = 32272kB
May 14 12:19:22 nanosoft kernel: [ 7315.873694] HighMem: 94*4kB 0*8kB 1*16kB 1*32kB 1*64kB 0*128kB 1*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 744kB
May 14 12:19:22 nanosoft kernel: [ 7315.873702] 3241 total pagecache pages
May 14 12:19:22 nanosoft kernel: [ 7315.873704] 40 pages in swap cache
May 14 12:19:22 nanosoft kernel: [ 7315.873706] Swap cache stats: add 263370, delete 263330, find 6585/8525
May 14 12:19:22 nanosoft kernel: [ 7315.873708] Free swap  = 0kB
May 14 12:19:22 nanosoft kernel: [ 7315.873710] Total swap = 931728kB
May 14 12:19:22 nanosoft kernel: [ 7315.881574] 458464 pages RAM
May 14 12:19:22 nanosoft kernel: [ 7315.881577] 232178 pages HighMem
May 14 12:19:22 nanosoft kernel: [ 7315.881579] 7942 pages reserved
May 14 12:19:22 nanosoft kernel: [ 7315.881580] 2777 pages shared
May 14 12:19:22 nanosoft kernel: [ 7315.881581] 437478 pages non-shared
```

---

### Post by pixel :-) on 2009-05-17
9.10 is beta, the current stable version is 9.04

---

