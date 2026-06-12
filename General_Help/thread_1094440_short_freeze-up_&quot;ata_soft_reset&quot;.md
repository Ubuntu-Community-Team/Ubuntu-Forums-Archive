---
title: "short freeze-up &quot;ata soft reset&quot;"
date: 2009-03-12
forum: General Help
---

### Post by AliTabuger7 on 2009-03-12
Every now and then my Ubuntu computer freezes up, so I looked through the system log application, and found this in kern.log and messeges.

I think one of my hard drives might be failing. How can I tell which one is ata1? Would that be sdb1?

The weird thing is that I did not have this problem until I did a complete reinstall of Ubuntu so that I could have 64 bit instead of 32 bit.

What do you think could be done to fix it? Just a filesystem error check or do I need to just replace it? It almost looks to me like its something else on the hard disk thats failing, not just a single sector.

```
 ata1: soft resetting link
 ata1.00: configured for PIO0
 ata1.01: configured for UDMA/33
 ata1: EH complete
 ata1: soft resetting link
 ata1.00: configured for PIO0
 ata1.01: configured for UDMA/33
 ata1: EH complete
 sd 0:0:1:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
 sd 0:0:1:0: [sda] Write Protect is off
 ata1: soft resetting link
 ata1.00: configured for PIO0
 ata1.01: configured for UDMA/33
 ata1: EH complete
 sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
 ata1: soft resetting link
 ata1.00: configured for PIO0
 ata1.01: configured for UDMA/33
 ata1: EH complete
 ata1: soft resetting link
 ata1.00: configured for PIO0
 ata1.01: configured for UDMA/33
 ata1: EH complete
 ata1: soft resetting link
 ata1.00: configured for PIO0
 ata1.01: configured for UDMA/33
 ata1: EH complete
 kjournald     D ffffffff80234069     0  2543      2
  ffff88018a1b5ce0 0000000000000046 ffff88018a29b920 ffff88018a29ba50
  ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400
  ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400
 Call Trace:
  [<ffffffff80501aa7>] io_schedule+0x37/0x50
  [<ffffffff803142f5>] sync_buffer+0x45/0x50
  [<ffffffff805020b2>] __wait_on_bit+0x62/0x90
  [<ffffffff803142b0>] ? sync_buffer+0x0/0x50
  [<ffffffff803142b0>] ? sync_buffer+0x0/0x50
  [<ffffffff80502159>] out_of_line_wait_on_bit+0x79/0x90
  [<ffffffff802670a0>] ? wake_bit_function+0x0/0x50
  [<ffffffff803146d6>] __wait_on_buffer+0x26/0x30
  [<ffffffffa01ef188>] journal_commit_transaction+0x728/0xd00 [jbd]
  [<ffffffff8025a85b>] ? lock_timer_base+0x3b/0x70
  [<ffffffff8025a8ef>] ? try_to_del_timer_sync+0x5f/0x70
  [<ffffffffa01f2ed9>] kjournald+0xe9/0x250 [jbd]
  [<ffffffff80267060>] ? autoremove_wake_function+0x0/0x40
  [<ffffffffa01f2df0>] ? kjournald+0x0/0x250 [jbd]
  [<ffffffff80266c2e>] kthread+0x4e/0x90
  [<ffffffff80213c99>] child_rip+0xa/0x11
  [<ffffffff80266be0>] ? kthread+0x0/0x90
  [<ffffffff80213c8f>] ? child_rip+0x0/0x11
 
 trackerd      D ffff88018a18d424     0  8300   7675
  ffff88011fc49cd8 0000000000000086 0000000000000246 ffffffff80234069
  ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400
  ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400
 Call Trace:
  [<ffffffff80234069>] ? __phys_addr+0x9/0x50
  [<ffffffffa01f2375>] log_wait_commit+0xc5/0x140 [jbd]
  [<ffffffff80267060>] ? autoremove_wake_function+0x0/0x40
  [<ffffffff8023de0e>] ? __wake_up+0x4e/0x70
  [<ffffffffa01ec1f5>] journal_stop+0x175/0x210 [jbd]
  [<ffffffffa01ecaf9>] journal_force_commit+0x29/0x30 [jbd]
  [<ffffffffa020d7c7>] ext3_force_commit+0x37/0x40 [ext3]
  [<ffffffffa0202424>] ext3_write_inode+0x44/0x60 [ext3]
  [<ffffffff8030efc5>] __sync_single_inode+0x215/0x2f0
  [<ffffffff8030f0f8>] __writeback_single_inode+0x58/0x1b0
  [<ffffffff8030f286>] sync_inode+0x36/0x60
  [<ffffffffa0200e2c>] ext3_sync_file+0xbc/0xe0 [ext3]
  [<ffffffff80312f81>] do_fsync+0x71/0xf0
  [<ffffffff80313036>] __do_fsync+0x36/0x50
  [<ffffffff80313080>] sys_fsync+0x10/0x20
  [<ffffffff8021285a>] system_call_fastpath+0x16/0x1b
 
 firefox       D ffff88018a18d424     0 21550      1
  ffff88010f4f1cd8 0000000000000086 0000000000000086 ffff88018a5c59c0
  ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400
  ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400
 Call Trace:
  [<ffffffffa01f2375>] log_wait_commit+0xc5/0x140 [jbd]
  [<ffffffff80267060>] ? autoremove_wake_function+0x0/0x40
  [<ffffffffa01ec1f5>] journal_stop+0x175/0x210 [jbd]
  [<ffffffffa01ecaf9>] journal_force_commit+0x29/0x30 [jbd]
  [<ffffffffa020d7c7>] ext3_force_commit+0x37/0x40 [ext3]
  [<ffffffffa0202424>] ext3_write_inode+0x44/0x60 [ext3]
  [<ffffffff8030efc5>] __sync_single_inode+0x215/0x2f0
  [<ffffffff8030f0f8>] __writeback_single_inode+0x58/0x1b0
  [<ffffffff8030f286>] sync_inode+0x36/0x60
  [<ffffffffa0200e2c>] ext3_sync_file+0xbc/0xe0 [ext3]
  [<ffffffff80312f81>] do_fsync+0x71/0xf0
  [<ffffffff80313036>] __do_fsync+0x36/0x50
  [<ffffffff80313080>] sys_fsync+0x10/0x20
  [<ffffffff8021285a>] system_call_fastpath+0x16/0x1b
 
 ata1: soft resetting link
 ata1.00: configured for PIO0
 ata1.01: configured for UDMA/33
 ata1: EH complete
 ata1: soft resetting link
 ata1.00: configured for PIO0
 ata1.01: configured for UDMA/33
 ata1: EH complete
 sd 0:0:1:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
 ata1: soft resetting link
 ata1.00: configured for PIO0
 ata1.01: configured for UDMA/33
 ata1: EH complete
 sd 0:0:1:0: [sda] Write Protect is off
 sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
 sd 0:0:1:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
 sd 0:0:1:0: [sda] Write Protect is off
 sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
```

---

