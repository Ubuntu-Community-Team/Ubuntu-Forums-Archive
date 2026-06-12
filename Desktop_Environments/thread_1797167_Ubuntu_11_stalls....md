---
title: "Ubuntu 11 stalls..."
date: 2011-07-04
forum: Desktop Environments
---

### Post by huntkey on 2011-07-04
Hi experts,

Recently I have been suffering the problem more and more. When it happens, my x11vnc session still gives me the desktop. I can still change between the workspace. When I click on an icon it still highlights it. However I can't run any programs. There is no response when I click on the task bar (I'm using the classic menu).

I can still get the SSH session open. It can still deny me if I type in the wrong password. However if I type in the correct password it will hang there and eventually I got "software cause connection aborted" error. (I use putty on my Windows laptop to connect with the ubuntu).

On my existing SSH sessions or already opened terminal window, I can't do "sudo" anymore. It will hang there after I type in the correct password.

I usually have to reboot the machine and everything will be fine.

However I want to know what's causing this... Right now I'm having the issue. I still have one old SSH session running. However I can't do "sudo"... What should I do to collect or even fix the issue? I will have my physical access to my PC tonight.

thanks!
Difan

---

### Post by huntkey on 2011-07-04
I just ran a dmsg and I got errors related to harddrive from what I see. Is this caused by harddrive failure? How do I check the harddrive for errors?
```

[333792.284785] ata1: lost interrupt (Status 0x50)
[333792.284806] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[333792.284810] ata1.00: failed command: WRITE DMA
[333792.284815] ata1.00: cmd ca/00:10:60:08:24/00:00:00:00:00/ef tag 0 dma 8192 out
[333792.284816]          res 40/00:00:00:4f:c2/00:00:00:00:00/40 Emask 0x4 (timeout)
[333792.284819] ata1.00: status: { DRDY }
[333792.284829] ata1.00: hard resetting link
[333792.618187] ata1.01: hard resetting link
[333793.127085] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[333793.127097] ata1.01: SATA link down (SStatus 0 SControl 300)
[333794.285061] ata2: lost interrupt (Status 0x58)
[333794.285079] ata2: drained 8 bytes to clear DRQ.
[333794.285093] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[333794.285098] sr 1:0:0:0: CDB: Get event status notification: 4a 01 00 00 10 00 00 00 08 00
[333794.285107] ata2.00: cmd a0/00:00:00:08:00/00:00:00:00:00/a0 tag 0 pio 16392 in
[333794.285108]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[333794.285111] ata2.00: status: { DRDY }
[333794.285119] ata2.00: hard resetting link
[333794.635944] ata2.01: hard resetting link
[333795.144840] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[333795.144854] ata2.01: SATA link down (SStatus 0 SControl 300)
[333795.144869] ata2.01: link offline, clearing class 3 to NONE
[333795.215119] ata2.00: configured for UDMA/100
[333798.162759] ata1.00: qc timeout (cmd 0x27)
[333798.162764] ata1.00: failed to read native max address (err_mask=0x4)
[333798.162767] ata1.00: HPA support seems broken, skipping HPA handling
[333798.162771] ata1.00: revalidation failed (errno=-5)
[333798.162783] ata1.00: hard resetting link
[333798.513676] ata1.01: hard resetting link
[333799.022561] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[333799.022577] ata1.01: SATA link down (SStatus 0 SControl 300)
[333799.092872] ata1.00: configured for UDMA/133
[333800.215758] ata2.00: qc timeout (cmd 0xa0)
[333800.215762] ata2.00: TEST_UNIT_READY failed (err_mask=0x5)
[333800.215770] ata2.00: hard resetting link
[333800.566597] ata2.01: hard resetting link
[333801.075512] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[333801.075533] ata2.01: SATA link down (SStatus 0 SControl 300)
[333801.075545] ata2.01: link offline, clearing class 3 to NONE
[333801.145674] ata2.00: configured for UDMA/100
[333804.093350] ata1.00: qc timeout (cmd 0xef)
[333804.093354] ata1.00: failed to disable DIPM, Emask 0x4
[333804.093355] ata1.00: disabling LPM on the link
[333804.093360] ata1.00: limiting SATA link speed to 1.5 Gbps
[333804.093363] ata1.00: limiting speed to UDMA/133:PIO3
[333804.093369] ata1.00: hard resetting link
[333804.444195] ata1.01: hard resetting link
[333804.953107] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[333804.953123] ata1.01: SATA link down (SStatus 0 SControl 300)
[333805.023402] ata1.00: configured for UDMA/133
[333805.023422] ata1.00: device reported invalid CHS sector 0
[333805.023432] ata1: EH complete
[333806.146164] ata2.00: qc timeout (cmd 0xa0)
[333806.146170] ata2.00: TEST_UNIT_READY failed (err_mask=0x5)
[333806.146175] ata2.00: limiting SATA link speed to 1.5 Gbps
[333806.146177] ata2.00: limiting speed to UDMA/100:PIO3
[333806.146185] ata2.00: hard resetting link
[333806.479586] ata2.01: hard resetting link
[333806.988585] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[333806.988598] ata2.01: SATA link down (SStatus 0 SControl 300)
[333806.988608] ata2.01: link offline, clearing class 3 to NONE
[333807.058725] ata2.00: configured for UDMA/100
[333812.059248] ata2.00: qc timeout (cmd 0xa0)
[333812.059252] ata2.00: TEST_UNIT_READY failed (err_mask=0x5)
[333812.059254] ata2.00: disabled
[333812.059284] ata2.00: hard resetting link
[333812.410114] ata2.01: hard resetting link
[333812.919093] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[333812.919111] ata2.01: SATA link down (SStatus 0 SControl 300)
[333812.919126] ata2.01: link offline, clearing class 3 to NONE
[333812.919159] ata2: EH complete
[333835.307799] ata1: lost interrupt (Status 0x50)
[333835.307827] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[333835.307832] ata1.00: failed command: WRITE DMA
[333835.307840] ata1.00: cmd ca/00:10:60:08:24/00:00:00:00:00/ef tag 0 dma 8192 out
[333835.307841]          res 40/00:00:00:4f:c2/00:00:00:00:00/40 Emask 0x4 (timeout)
[333835.307845] ata1.00: status: { DRDY }
[333835.307854] ata1.00: hard resetting link
[333835.658694] ata1.01: hard resetting link
[333836.167667] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[333836.167683] ata1.01: SATA link down (SStatus 0 SControl 300)
[333836.237896] ata1.00: configured for UDMA/133
[333836.237905] ata1.00: device reported invalid CHS sector 0
[333836.237913] ata1: EH complete
[333866.329214] ata1: lost interrupt (Status 0x50)
[333866.329236] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[333866.329240] ata1.00: failed command: WRITE DMA
[333866.329244] ata1.00: cmd ca/00:10:60:08:24/00:00:00:00:00/ef tag 0 dma 8192 out
[333866.329245]          res 40/00:00:00:4f:c2/00:00:00:00:00/40 Emask 0x4 (timeout)
[333866.329247] ata1.00: status: { DRDY }
[333866.329254] ata1.00: hard resetting link
[333866.662570] ata1.01: hard resetting link
[333867.171497] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[333867.171510] ata1.01: SATA link down (SStatus 0 SControl 300)
[333867.241729] ata1.00: configured for UDMA/133
[333867.241740] ata1.00: device reported invalid CHS sector 0
[333867.241749] ata1: EH complete
[333898.157901] ata1: lost interrupt (Status 0x50)
[333898.157927] ata1.00: limiting speed to UDMA/100:PIO3
[333898.157934] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[333898.157940] ata1.00: failed command: WRITE DMA
[333898.157947] ata1.00: cmd ca/00:10:60:08:24/00:00:00:00:00/ef tag 0 dma 8192 out
[333898.157949]          res 40/00:00:00:4f:c2/00:00:00:00:00/40 Emask 0x4 (timeout)
[333898.157954] ata1.00: status: { DRDY }
[333898.157963] ata1.00: hard resetting link
[333898.508805] ata1.01: hard resetting link
[333899.017599] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[333899.017612] ata1.01: SATA link down (SStatus 0 SControl 300)
[333899.087920] ata1.00: configured for UDMA/100
[333899.087930] ata1.00: device reported invalid CHS sector 0
[333899.087941] ata1: EH complete
[333925.108534] INFO: task jbd2/sda2-8:267 blocked for more than 120 seconds.
[333925.108539] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[333925.108544] jbd2/sda2-8     D 0000000000000000     0   267      2 0x00000000
[333925.108550]  ffff8801af1c7d20 0000000000000046 ffff8801af1c7fd8 ffff8801af1c6000
[333925.108556]  0000000000013d00 ffff8801aed93178 ffff8801af1c7fd8 0000000000013d00
[333925.108563]  ffffffff81a0b020 ffff8801aed92dc0 0000000000000002 ffff880036ffd0a0
[333925.108570] Call Trace:
[333925.108581]  [<ffffffff81242d40>] jbd2_journal_commit_transaction+0x1b0/0x1190
[333925.108591]  [<ffffffff8100a6e0>] ? __switch_to+0xc0/0x2f0
[333925.108600]  [<ffffffff815c2cbe>] ? _raw_spin_lock+0xe/0x20
[333925.108608]  [<ffffffff81074fdb>] ? lock_timer_base.clone.20+0x3b/0x70
[333925.108613]  [<ffffffff81087f30>] ? autoremove_wake_function+0x0/0x40
[333925.108619]  [<ffffffff81247e8b>] kjournald2+0xbb/0x220
[333925.108623]  [<ffffffff81087f30>] ? autoremove_wake_function+0x0/0x40
[333925.108626]  [<ffffffff81247dd0>] ? kjournald2+0x0/0x220
[333925.108630]  [<ffffffff810877e6>] kthread+0x96/0xa0
[333925.108634]  [<ffffffff8100ce24>] kernel_thread_helper+0x4/0x10
[333925.108638]  [<ffffffff81087750>] ? kthread+0x0/0xa0
[333925.108641]  [<ffffffff8100ce20>] ? kernel_thread_helper+0x0/0x10
[333925.108646] INFO: task jbd2/sda6-8:751 blocked for more than 120 seconds.
[333925.108648] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[333925.108651] jbd2/sda6-8     D ffffffff8104e80e     0   751      2 0x00000000
[333925.108655]  ffff8801af289c20 0000000000000046 ffff8801af289fd8 ffff8801af288000
[333925.108660]  0000000000013d00 ffff8801ae419a98 ffff8801af289fd8 0000000000013d00
[333925.108664]  ffff88015648adc0 ffff8801ae4196e0 ffff8800bf756868 ffff8800bf433d00
[333925.108668] Call Trace:
[333925.108674]  [<ffffffff81191db0>] ? sync_buffer+0x0/0x50
[333925.108678]  [<ffffffff815c0980>] io_schedule+0x70/0xc0
[333925.108682]  [<ffffffff81191df0>] sync_buffer+0x40/0x50
[333925.108686]  [<ffffffff815c12ff>] __wait_on_bit+0x5f/0x90
[333925.108690]  [<ffffffff81191db0>] ? sync_buffer+0x0/0x50
[333925.108694]  [<ffffffff815c13ac>] out_of_line_wait_on_bit+0x7c/0x90
[333925.108698]  [<ffffffff81087f70>] ? wake_bit_function+0x0/0x50
[333925.108702]  [<ffffffff81191dae>] __wait_on_buffer+0x2e/0x30
[333925.108705]  [<ffffffff812432ef>] jbd2_journal_commit_transaction+0x75f/0x1190
[333925.108711]  [<ffffffff81076185>] ? try_to_del_timer_sync+0x85/0xe0
[333925.108714]  [<ffffffff81247e8b>] kjournald2+0xbb/0x220
[333925.108718]  [<ffffffff81087f30>] ? autoremove_wake_function+0x0/0x40
[333925.108722]  [<ffffffff81247dd0>] ? kjournald2+0x0/0x220
[333925.108725]  [<ffffffff810877e6>] kthread+0x96/0xa0
[333925.108729]  [<ffffffff8100ce24>] kernel_thread_helper+0x4/0x10
[333925.108733]  [<ffffffff81087750>] ? kthread+0x0/0xa0
[333925.108736]  [<ffffffff8100ce20>] ? kernel_thread_helper+0x0/0x10
[333925.108740] INFO: task rsyslogd:791 blocked for more than 120 seconds.
[333925.108742] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[333925.108744] rsyslogd        D 0000000000000000     0   791      1 0x00000000
[333925.108748]  ffff8801acbe78e8 0000000000000082 ffff8801acbe7fd8 ffff8801acbe6000
[333925.108753]  0000000000013d00 ffff8801ac40df38 ffff8801acbe7fd8 0000000000013d00
[333925.108757]  ffff88019ab22dc0 ffff8801ac40db80 ffff8800bf754fd8 ffff8800bf413d00
[333925.108761] Call Trace:
[333925.108766]  [<ffffffff81191db0>] ? sync_buffer+0x0/0x50
[333925.108769]  [<ffffffff815c0980>] io_schedule+0x70/0xc0
[333925.108773]  [<ffffffff81191df0>] sync_buffer+0x40/0x50
[333925.108777]  [<ffffffff815c11aa>] __wait_on_bit_lock+0x5a/0xc0
[333925.108782]  [<ffffffff8108b9b0>] ? hrtimer_wakeup+0x0/0x30
[333925.108786]  [<ffffffff81191db0>] ? sync_buffer+0x0/0x50
[333925.108790]  [<ffffffff815c128c>] out_of_line_wait_on_bit_lock+0x7c/0x90
[333925.108794]  [<ffffffff81087f70>] ? wake_bit_function+0x0/0x50
[333925.108798]  [<ffffffff81192479>] ? bh_lru_install+0x129/0x160
[333925.108802]  [<ffffffff81191e36>] __lock_buffer+0x36/0x40
[333925.108807]  [<ffffffff81241f5a>] do_get_write_access+0x3fa/0x490
[333925.108811]  [<ffffffff81193c46>] ? __getblk+0x36/0x70
[333925.108816]  [<ffffffff81209e2d>] ? ext4_dirty_inode+0x3d/0x60
[333925.108821]  [<ffffffff81242131>] jbd2_journal_get_write_access+0x31/0x50
[333925.108826]  [<ffffffff81228f9e>] __ext4_journal_get_write_access+0x3e/0x80
[333925.108830]  [<ffffffff81205268>] ext4_reserve_inode_write+0x78/0xa0
[333925.108834]  [<ffffffff812052df>] ext4_mark_inode_dirty+0x4f/0x220
[333925.108838]  [<ffffffff8121dc03>] ? ext4_journal_start_sb+0xb3/0x140
[333925.108842]  [<ffffffff81209e2d>] ext4_dirty_inode+0x3d/0x60
[333925.108846]  [<ffffffff8118b31f>] __mark_inode_dirty+0x3f/0x260
[333925.108851]  [<ffffffff8117f0b5>] file_update_time+0xf5/0x170
[333925.108857]  [<ffffffff8110d928>] __generic_file_aio_write+0x1f8/0x440
[333925.108862]  [<ffffffff8110dbd6>] generic_file_aio_write+0x66/0xd0
[333925.108866]  [<ffffffff811fe2a9>] ext4_file_write+0x69/0x280
[333925.108870]  [<ffffffff81164682>] do_sync_write+0xd2/0x110
[333925.108874]  [<ffffffff811406d1>] ? free_pages_and_swap_cache+0xb1/0xe0
[333925.108879]  [<ffffffff81013859>] ? read_tsc+0x9/0x20
[333925.108883]  [<ffffffff81092eb1>] ? ktime_get_ts+0xb1/0xf0
[333925.108888]  [<ffffffff812ae7e8>] ? apparmor_file_permission+0x18/0x20
[333925.108893]  [<ffffffff81279bac>] ? security_file_permission+0x2c/0xb0
[333925.108897]  [<ffffffff81164ab1>] ? rw_verify_area+0x61/0xf0
[333925.108901]  [<ffffffff81164df6>] vfs_write+0xc6/0x180
[333925.108904]  [<ffffffff81165111>] sys_write+0x51/0x90
[333925.108908]  [<ffffffff815c402e>] ? do_device_not_available+0xe/0x10
[333925.108912]  [<ffffffff8100c002>] system_call_fastpath+0x16/0x1b
[333925.108933] INFO: task flush-8:0:1616 blocked for more than 120 seconds.
[333925.108936] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[333925.108938] flush-8:0       D 0000000000000001     0  1616      2 0x00000000
[333925.108942]  ffff88018fb3f990 0000000000000046 ffff88018fb3ffd8 ffff88018fb3e000
[333925.108947]  0000000000013d00 ffff88019a5583b8 ffff88018fb3ffd8 0000000000013d00
[333925.108951]  ffff88016842adc0 ffff88019a558000 000000000000000e ffff8801af976000
[333925.108955] Call Trace:
[333925.108960]  [<ffffffff812405f2>] start_this_handle.clone.7+0x362/0x4a0
[333925.108964]  [<ffffffff81087f30>] ? autoremove_wake_function+0x0/0x40
[333925.108968]  [<ffffffff812407fa>] jbd2__journal_start+0xca/0x110
[333925.108972]  [<ffffffff81240853>] jbd2_journal_start+0x13/0x20
[333925.108976]  [<ffffffff8121dc03>] ext4_journal_start_sb+0xb3/0x140
[333925.108981]  [<ffffffff81118b76>] ? __pagevec_release+0x26/0x40
[333925.108985]  [<ffffffff81202fb5>] ? ext4_meta_trans_blocks+0x75/0xe0
[333925.108989]  [<ffffffff81209727>] ext4_da_writepages+0x2b7/0x630
[333925.108994]  [<ffffffff81117151>] do_writepages+0x21/0x40
[333925.108998]  [<ffffffff8118b5df>] writeback_single_inode+0x9f/0x240
[333925.109002]  [<ffffffff8118b9cb>] writeback_sb_inodes+0xcb/0x160
[333925.109006]  [<ffffffff8118bc1b>] writeback_inodes_wb+0x10b/0x1c0
[333925.109010]  [<ffffffff8118c04e>] wb_writeback+0x37e/0x490
[333925.109014]  [<ffffffff815c2e6f>] ? _raw_spin_lock_irqsave+0x2f/0x40
[333925.109019]  [<ffffffff81074fdb>] ? lock_timer_base.clone.20+0x3b/0x70
[333925.109023]  [<ffffffff8118c381>] wb_do_writeback+0x221/0x230
[333925.109028]  [<ffffffff8118c412>] bdi_writeback_thread+0x82/0x260
[333925.109032]  [<ffffffff8118c390>] ? bdi_writeback_thread+0x0/0x260
[333925.109035]  [<ffffffff810877e6>] kthread+0x96/0xa0
[333925.109039]  [<ffffffff8100ce24>] kernel_thread_helper+0x4/0x10
[333925.109043]  [<ffffffff81087750>] ? kthread+0x0/0xa0
[333925.109046]  [<ffffffff8100ce20>] ? kernel_thread_helper+0x0/0x10
[333925.109052] INFO: task vmware-hostd:30612 blocked for more than 120 seconds.
[333925.109054] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[333925.109056] vmware-hostd    D 0000000000000001     0 30612      1 0x00000000
[333925.109060]  ffff88016b897a58 0000000000000086 ffff88016b897fd8 ffff88016b896000
[333925.109064]  0000000000013d00 ffff8801564a03b8 ffff88016b897fd8 0000000000013d00
[333925.109069]  ffff88016842adc0 ffff8801564a0000 ffff88016b897af8 ffff8801af976000
[333925.109073] Call Trace:
[333925.109077]  [<ffffffff812405f2>] start_this_handle.clone.7+0x362/0x4a0
[333925.109081]  [<ffffffff81087f30>] ? autoremove_wake_function+0x0/0x40
[333925.109086]  [<ffffffff812407fa>] jbd2__journal_start+0xca/0x110
[333925.109090]  [<ffffffff81240853>] jbd2_journal_start+0x13/0x20
[333925.109094]  [<ffffffff8121dc03>] ext4_journal_start_sb+0xb3/0x140
[333925.109098]  [<ffffffff81209e17>] ext4_dirty_inode+0x27/0x60
[333925.109101]  [<ffffffff8118b31f>] __mark_inode_dirty+0x3f/0x260
[333925.109105]  [<ffffffff8117f0b5>] file_update_time+0xf5/0x170
[333925.109110]  [<ffffffff8110d928>] __generic_file_aio_write+0x1f8/0x440
[333925.109115]  [<ffffffff811bfbb0>] ? proc_reg_open+0x0/0x1a0
[333925.109119]  [<ffffffff81162e4f>] ? __dentry_open+0x22f/0x2f0
[333925.109124]  [<ffffffff8110dbd6>] generic_file_aio_write+0x66/0xd0
[333925.109127]  [<ffffffff811fe2a9>] ext4_file_write+0x69/0x280
[333925.109131]  [<ffffffff81164682>] do_sync_write+0xd2/0x110
[333925.109136]  [<ffffffff811815ee>] ? vfsmount_lock_local_unlock+0x1e/0x30
[333925.109141]  [<ffffffff812ae7e8>] ? apparmor_file_permission+0x18/0x20
[333925.109145]  [<ffffffff81279bac>] ? security_file_permission+0x2c/0xb0
[333925.109149]  [<ffffffff81164ab1>] ? rw_verify_area+0x61/0xf0
[333925.109152]  [<ffffffff81164df6>] vfs_write+0xc6/0x180
[333925.109156]  [<ffffffff81165111>] sys_write+0x51/0x90
[333925.109159]  [<ffffffff8100c002>] system_call_fastpath+0x16/0x1b
[333925.109163] INFO: task indicator-apple:621 blocked for more than 120 seconds.
[333925.109165] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[333925.109168] indicator-apple D 0000000000000005     0   621      1 0x00000000
[333925.109172]  ffff88018bc87a58 0000000000000082 ffff88018bc87fd8 ffff88018bc86000
[333925.109176]  0000000000013d00 ffff88013c99c858 ffff88018bc87fd8 0000000000013d00
[333925.109180]  ffff8801b31a96e0 ffff88013c99c4a0 0000000000000000 ffff8801af976000
[333925.109185] Call Trace:
[333925.109189]  [<ffffffff812405f2>] start_this_handle.clone.7+0x362/0x4a0
[333925.109193]  [<ffffffff81087f30>] ? autoremove_wake_function+0x0/0x40
[333925.109197]  [<ffffffff812407fa>] jbd2__journal_start+0xca/0x110
[333925.109202]  [<ffffffff81240853>] jbd2_journal_start+0x13/0x20
[333925.109205]  [<ffffffff8121dc03>] ext4_journal_start_sb+0xb3/0x140
[333925.109209]  [<ffffffff81209e17>] ext4_dirty_inode+0x27/0x60
[333925.109213]  [<ffffffff8118b31f>] __mark_inode_dirty+0x3f/0x260
[333925.109217]  [<ffffffff8117f0b5>] file_update_time+0xf5/0x170
[333925.109222]  [<ffffffff8110d928>] __generic_file_aio_write+0x1f8/0x440
[333925.109226]  [<ffffffff8110dbd6>] generic_file_aio_write+0x66/0xd0
[333925.109230]  [<ffffffff811fe2a9>] ext4_file_write+0x69/0x280
[333925.109234]  [<ffffffff81164682>] do_sync_write+0xd2/0x110
[333925.109239]  [<ffffffff812ae7e8>] ? apparmor_file_permission+0x18/0x20
[333925.109243]  [<ffffffff81279bac>] ? security_file_permission+0x2c/0xb0
[333925.109247]  [<ffffffff81164ab1>] ? rw_verify_area+0x61/0xf0
[333925.109250]  [<ffffffff81164df6>] vfs_write+0xc6/0x180
[333925.109254]  [<ffffffff81165111>] sys_write+0x51/0x90
[333925.109258]  [<ffffffff8100c002>] system_call_fastpath+0x16/0x1b
[333925.109269] INFO: task kworker/7:2:18161 blocked for more than 120 seconds.
[333925.109271] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[333925.109273] kworker/7:2     D 0000000000000007     0 18161      2 0x00000000
[333925.109277]  ffff8801564abd30 0000000000000046 ffff8801564abfd8 ffff8801564aa000
[333925.109282]  0000000000013d00 ffff88013c9edf38 ffff8801564abfd8 0000000000013d00
[333925.109286]  ffff88016842c4a0 ffff88013c9edb80 ffff8801564abd10 ffff8801af93b0a8
[333925.109290] Call Trace:
[333925.109295]  [<ffffffff815c19f7>] __mutex_lock_slowpath+0xf7/0x180
[333925.109300]  [<ffffffff8104ef38>] ? hrtick_update+0x38/0x40
[333925.109304]  [<ffffffff815c144b>] mutex_lock+0x2b/0x50
[333925.109309]  [<ffffffff81409863>] ata_scsi_dev_rescan+0x33/0x130
[333925.109313]  [<ffffffff81409830>] ? ata_scsi_dev_rescan+0x0/0x130
[333925.109318]  [<ffffffff8108269d>] process_one_work+0x11d/0x420
[333925.109322]  [<ffffffff81083298>] worker_thread+0x168/0x360
[333925.109326]  [<ffffffff81083130>] ? worker_thread+0x0/0x360
[333925.109329]  [<ffffffff810877e6>] kthread+0x96/0xa0
[333925.109333]  [<ffffffff8100ce24>] kernel_thread_helper+0x4/0x10
[333925.109337]  [<ffffffff81087750>] ? kthread+0x0/0xa0
[333925.109340]  [<ffffffff8100ce20>] ? kernel_thread_helper+0x0/0x10
[333925.109352] INFO: task dynamips:27172 blocked for more than 120 seconds.
[333925.109354] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[333925.109357] dynamips        D 0000000000000002     0 27172  26724 0x00000000
[333925.109361]  ffff88016bb97a58 0000000000000086 ffff88016bb97fd8 ffff88016bb96000
[333925.109365]  0000000000013d00 ffff8801b311b178 ffff88016bb97fd8 0000000000013d00
[333925.109369]  ffff88013c99adc0 ffff8801b311adc0 ffff8800bf44f520 ffff8801af976000
[333925.109374] Call Trace:
[333925.109378]  [<ffffffff812405f2>] start_this_handle.clone.7+0x362/0x4a0
[333925.109382]  [<ffffffff81087f30>] ? autoremove_wake_function+0x0/0x40
[333925.109386]  [<ffffffff812407fa>] jbd2__journal_start+0xca/0x110
[333925.109390]  [<ffffffff81240853>] jbd2_journal_start+0x13/0x20
[333925.109394]  [<ffffffff8121dc03>] ext4_journal_start_sb+0xb3/0x140
[333925.109398]  [<ffffffff81209e17>] ext4_dirty_inode+0x27/0x60
[333925.109402]  [<ffffffff8118b31f>] __mark_inode_dirty+0x3f/0x260
[333925.109406]  [<ffffffff8117f0b5>] file_update_time+0xf5/0x170
[333925.109410]  [<ffffffff8110d928>] __generic_file_aio_write+0x1f8/0x440
[333925.109414]  [<ffffffff815c059c>] ? schedule+0x3ec/0x760
[333925.109418]  [<ffffffff8108bb90>] ? lock_hrtimer_base.clone.25+0x30/0x60
[333925.109423]  [<ffffffff8110dbd6>] generic_file_aio_write+0x66/0xd0
[333925.109427]  [<ffffffff811fe2a9>] ext4_file_write+0x69/0x280
[333925.109431]  [<ffffffff81164682>] do_sync_write+0xd2/0x110
[333925.109435]  [<ffffffff81099f9a>] ? get_futex_key+0x15a/0x1d0
[333925.109440]  [<ffffffff812ae7e8>] ? apparmor_file_permission+0x18/0x20
[333925.109444]  [<ffffffff81279bac>] ? security_file_permission+0x2c/0xb0
[333925.109448]  [<ffffffff81164ab1>] ? rw_verify_area+0x61/0xf0
[333925.109451]  [<ffffffff81164df6>] vfs_write+0xc6/0x180
[333925.109455]  [<ffffffff81165111>] sys_write+0x51/0x90
[333925.109458]  [<ffffffff815c402e>] ? do_device_not_available+0xe/0x10
[333925.109462]  [<ffffffff8100c002>] system_call_fastpath+0x16/0x1b
[333925.109467] INFO: task dynamips:27194 blocked for more than 120 seconds.
[333925.109469] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[333925.109471] dynamips        D 0000000000000004     0 27194  26724 0x00000000
[333925.109475]  ffff88019a4f7a58 0000000000000086 ffff88019a4f7fd8 ffff88019a4f6000
[333925.109480]  0000000000013d00 ffff88016b849a98 ffff88019a4f7fd8 0000000000013d00
[333925.109484]  ffff8801b318adc0 ffff88016b8496e0 0000000000000000 ffff8801af976000
[333925.109488] Call Trace:
[333925.109493]  [<ffffffff812405f2>] start_this_handle.clone.7+0x362/0x4a0
[333925.109497]  [<ffffffff81087f30>] ? autoremove_wake_function+0x0/0x40
[333925.109501]  [<ffffffff812407fa>] jbd2__journal_start+0xca/0x110
[333925.109505]  [<ffffffff81240853>] jbd2_journal_start+0x13/0x20
[333925.109509]  [<ffffffff8121dc03>] ext4_journal_start_sb+0xb3/0x140
[333925.109513]  [<ffffffff81209e17>] ext4_dirty_inode+0x27/0x60
[333925.109517]  [<ffffffff8118b31f>] __mark_inode_dirty+0x3f/0x260
[333925.109521]  [<ffffffff8117f0b5>] file_update_time+0xf5/0x170
[333925.109525]  [<ffffffff8110d928>] __generic_file_aio_write+0x1f8/0x440
[333925.109529]  [<ffffffff815c059c>] ? schedule+0x3ec/0x760
[333925.109533]  [<ffffffff8108bb90>] ? lock_hrtimer_base.clone.25+0x30/0x60
[333925.109538]  [<ffffffff8110dbd6>] generic_file_aio_write+0x66/0xd0
[333925.109541]  [<ffffffff811fe2a9>] ext4_file_write+0x69/0x280
[333925.109545]  [<ffffffff81164682>] do_sync_write+0xd2/0x110
[333925.109549]  [<ffffffff81099f9a>] ? get_futex_key+0x15a/0x1d0
[333925.109553]  [<ffffffff812ae7e8>] ? apparmor_file_permission+0x18/0x20
[333925.109558]  [<ffffffff81279bac>] ? security_file_permission+0x2c/0xb0
[333925.109561]  [<ffffffff81164ab1>] ? rw_verify_area+0x61/0xf0
[333925.109565]  [<ffffffff81164df6>] vfs_write+0xc6/0x180
[333925.109569]  [<ffffffff81165111>] sys_write+0x51/0x90
[333925.109572]  [<ffffffff815c402e>] ? do_device_not_available+0xe/0x10
[333925.109576]  [<ffffffff8100c002>] system_call_fastpath+0x16/0x1b
[333925.109579] INFO: task dynamips:27324 blocked for more than 120 seconds.
[333925.109581] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[333925.109584] dynamips        D 0000000000000006     0 27324  26724 0x00000000
[333925.109588]  ffff8800aa84ba58 0000000000000086 ffff8800aa84bfd8 ffff8800aa84a000
[333925.109592]  0000000000013d00 ffff8801684783b8 ffff8800aa84bfd8 0000000000013d00
[333925.109596]  ffff8801b31c0000 ffff880168478000 ffff8800bf4cf520 ffff8801af976000
[333925.109601] Call Trace:
[333925.109605]  [<ffffffff812405f2>] start_this_handle.clone.7+0x362/0x4a0
[333925.109609]  [<ffffffff81087f30>] ? autoremove_wake_function+0x0/0x40
[333925.109614]  [<ffffffff812407fa>] jbd2__journal_start+0xca/0x110
[333925.109618]  [<ffffffff81240853>] jbd2_journal_start+0x13/0x20
[333925.109622]  [<ffffffff8121dc03>] ext4_journal_start_sb+0xb3/0x140
[333925.109626]  [<ffffffff81209e17>] ext4_dirty_inode+0x27/0x60
[333925.109629]  [<ffffffff8118b31f>] __mark_inode_dirty+0x3f/0x260
[333925.109633]  [<ffffffff8117f0b5>] file_update_time+0xf5/0x170
[333925.109638]  [<ffffffff8110d928>] __generic_file_aio_write+0x1f8/0x440
[333925.109642]  [<ffffffff815c059c>] ? schedule+0x3ec/0x760
[333925.109646]  [<ffffffff8108bb90>] ? lock_hrtimer_base.clone.25+0x30/0x60
[333925.109650]  [<ffffffff8110dbd6>] generic_file_aio_write+0x66/0xd0
[333925.109654]  [<ffffffff811fe2a9>] ext4_file_write+0x69/0x280
[333925.109658]  [<ffffffff81164682>] do_sync_write+0xd2/0x110
[333925.109661]  [<ffffffff81099f9a>] ? get_futex_key+0x15a/0x1d0
[333925.109666]  [<ffffffff812ae7e8>] ? apparmor_file_permission+0x18/0x20
[333925.109670]  [<ffffffff81279bac>] ? security_file_permission+0x2c/0xb0
[333925.109674]  [<ffffffff81164ab1>] ? rw_verify_area+0x61/0xf0
[333925.109678]  [<ffffffff81164df6>] vfs_write+0xc6/0x180
[333925.109681]  [<ffffffff81165111>] sys_write+0x51/0x90
[333925.109685]  [<ffffffff815c402e>] ? do_device_not_available+0xe/0x10
[333925.109689]  [<ffffffff8100c002>] system_call_fastpath+0x16/0x1b
[333929.266978] ata1: lost interrupt (Status 0x50)
[333929.267003] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[333929.267010] ata1.00: failed command: WRITE DMA
[333929.267019] ata1.00: cmd ca/00:10:60:08:24/00:00:00:00:00/ef tag 0 dma 8192 out
[333929.267022]          res 40/00:00:00:4f:c2/00:00:00:00:00/40 Emask 0x4 (timeout)
[333929.267027] ata1.00: status: { DRDY }
[333929.267041] ata1.00: hard resetting link
[333929.617926] ata1.01: hard resetting link
[333930.126809] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[333930.126824] ata1.01: SATA link down (SStatus 0 SControl 300)
[333930.197069] ata1.00: configured for UDMA/100
[333930.197078] ata1.00: device reported invalid CHS sector 0
[333930.197089] ata1: EH complete
[333960.288434] ata1: lost interrupt (Status 0x50)
[333960.288458] ata1.00: limiting speed to UDMA/33:PIO3
[333960.288467] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[333960.288474] ata1.00: failed command: WRITE DMA
[333960.288485] ata1.00: cmd ca/00:10:60:08:24/00:00:00:00:00/ef tag 0 dma 8192 out
[333960.288487]          res 40/00:00:00:4f:c2/00:00:00:00:00/40 Emask 0x4 (timeout)
[333960.288492] ata1.00: status: { DRDY }
[333960.288502] ata1.00: hard resetting link
[333960.639355] ata1.01: hard resetting link
[333961.148304] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[333961.148318] ata1.01: SATA link down (SStatus 0 SControl 300)
[333961.218552] ata1.00: configured for UDMA/33
[333961.218559] ata1.00: device reported invalid CHS sector 0
[333961.218567] sd 0:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[333961.218569] sd 0:0:0:0: [sda]  Sense Key : Aborted Command [current] [descriptor]
[333961.218572] Descriptor sense data with sense descriptors (in hex):
[333961.218573]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00
[333961.218578]         00 00 00 00
[333961.218580] sd 0:0:0:0: [sda]  Add. Sense: No additional sense information
[333961.218582] sd 0:0:0:0: [sda] CDB: Write(10): 2a 00 0f 24 08 60 00 00 10 00
[333961.218593] end_request: I/O error, dev sda, sector 254019680
[333961.218598] quiet_error: 51 callbacks suppressed
[333961.218601] Buffer I/O error on device sda2, logical block 12058636
[333961.218603] lost page write due to I/O error on sda2
[333961.218609] Buffer I/O error on device sda2, logical block 12058637
[333961.218612] lost page write due to I/O error on sda2
[333961.218626] ata1: EH complete
[333992.187207] ata1: lost interrupt (Status 0x50)
[333992.187233] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[333992.187240] ata1.00: failed command: WRITE DMA
[333992.187250] ata1.00: cmd ca/00:10:30:11:64/00:00:00:00:00/ef tag 0 dma 8192 out
[333992.187252]          res 40/00:00:00:4f:c2/00:00:00:00:00/40 Emask 0x4 (timeout)
[333992.187257] ata1.00: status: { DRDY }
[333992.187268] ata1.00: hard resetting link
[333992.538169] ata1.01: hard resetting link
[333993.047016] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[333993.047033] ata1.01: SATA link down (SStatus 0 SControl 300)
[333993.117264] ata1.00: configured for UDMA/33
[333993.117272] ata1.00: device reported invalid CHS sector 0
[333993.117281] ata1: EH complete
[334024.173743] ata1: lost interrupt (Status 0x50)
[334024.173770] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[334024.173777] ata1.00: failed command: WRITE DMA
[334024.173789] ata1.00: cmd ca/00:10:30:11:64/00:00:00:00:00/ef tag 0 dma 8192 out
[334024.173791]          res 40/00:00:00:4f:c2/00:00:00:00:00/40 Emask 0x4 (timeout)
```

---

### Post by huntkey on 2011-07-04
Thank you Overdrank for formatting my post!

Just to add some more information. The problem seems start to happen after I have the vmware server 2 installed. It might be a coincidence but just in case it might be related...

---

### Post by huntkey on 2011-07-05
It happened again tonight. The mouse became very slow responding. The "top" command hang. The "ps aux" worked but no process was using above 7% CPU. Weird thing is that the "fdisk -l" showed me no partitions at all while "df -a" still shows all of them. Then I tried to reboot the PC with "reboot" command but it returned "INPUT/OUTPUT error". 

Then I hard reset the PC. After it came backup I ran the disk check with command "smartctl -t short" and "smartctl -t long". They all report no errors. I'm really stuck here... Please advice! Thanks!

---

