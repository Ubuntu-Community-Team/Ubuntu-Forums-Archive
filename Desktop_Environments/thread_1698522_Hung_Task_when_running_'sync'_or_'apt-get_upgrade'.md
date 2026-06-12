---
title: "Hung Task when running 'sync' or 'apt-get upgrade'"
date: 2011-03-02
forum: Desktop Environments
---

### Post by darkpixel on 2011-03-02
I've run into this odd behavior the last two days.
When I do an 'apt-get update && apt-get upgrade' the procedure will hang at some random point while installing updates.

I get this in the syslog:

[46083.428896] INFO: task dpkg:26336 blocked for more than 120 seconds.
[46083.428902] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[46083.428905] dpkg          D 0000000100458eee     0 26336  25929 0x00000000
[46083.428911]  ffff88020e3f5cf8 0000000000000082 ffff88020e3f5dc0 0000000000015980
[46083.428916]  ffff88020e3f5fd8 0000000000015980 ffff88020e3f5fd8 ffff880235e496e0
[46083.428920]  0000000000015980 0000000000015980 ffff88020e3f5fd8 0000000000015980
[46083.428925] Call Trace:
[46083.428937]  [<ffffffff81588c7d>] schedule_timeout+0x22d/0x310
[46083.428946]  [<ffffffff8104edc2>] ? enqueue_entity+0x132/0x1b0
[46083.428950]  [<ffffffff8104f283>] ? enqueue_task_fair+0x43/0x90
[46083.428955]  [<ffffffff81052cf7>] ? enqueue_task+0x77/0x90
[46083.428958]  [<ffffffff8158885b>] wait_for_common+0xdb/0x180
[46083.428962]  [<ffffffff81056a00>] ? default_wake_function+0x0/0x20
[46083.428966]  [<ffffffff815889dd>] wait_for_completion+0x1d/0x20
[46083.428974]  [<ffffffff811762a9>] sync_inodes_sb+0x89/0xc0
[46083.428978]  [<ffffffff8117acf0>] ? sync_one_sb+0x0/0x30
[46083.428981]  [<ffffffff8117acd8>] __sync_filesystem+0x88/0xa0
[46083.428984]  [<ffffffff8117ad10>] sync_one_sb+0x20/0x30
[46083.428991]  [<ffffffff8115550b>] iterate_supers+0x8b/0xd0
[46083.428994]  [<ffffffff8117ad65>] sys_sync+0x45/0x70
[46083.429002]  [<ffffffff8100a0f2>] system_call_fastpath+0x16/0x1b
[46203.433092] INFO: task dpkg:26336 blocked for more than 120 seconds.
[46203.433097] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[46203.433100] dpkg          D 0000000100458eee     0 26336  25929 0x00000000
[46203.433105]  ffff88020e3f5cf8 0000000000000082 ffff88020e3f5dc0 0000000000015980
[46203.433109]  ffff88020e3f5fd8 0000000000015980 ffff88020e3f5fd8 ffff880235e496e0
[46203.433112]  0000000000015980 0000000000015980 ffff88020e3f5fd8 0000000000015980
[46203.433115] Call Trace:
[46203.433127]  [<ffffffff81588c7d>] schedule_timeout+0x22d/0x310
[46203.433135]  [<ffffffff8104edc2>] ? enqueue_entity+0x132/0x1b0
[46203.433138]  [<ffffffff8104f283>] ? enqueue_task_fair+0x43/0x90
[46203.433142]  [<ffffffff81052cf7>] ? enqueue_task+0x77/0x90
[46203.433144]  [<ffffffff8158885b>] wait_for_common+0xdb/0x180
[46203.433148]  [<ffffffff81056a00>] ? default_wake_function+0x0/0x20
[46203.433151]  [<ffffffff815889dd>] wait_for_completion+0x1d/0x20
[46203.433157]  [<ffffffff811762a9>] sync_inodes_sb+0x89/0xc0
[46203.433161]  [<ffffffff8117acf0>] ? sync_one_sb+0x0/0x30
[46203.433163]  [<ffffffff8117acd8>] __sync_filesystem+0x88/0xa0
[46203.433166]  [<ffffffff8117ad10>] sync_one_sb+0x20/0x30
[46203.433171]  [<ffffffff8115550b>] iterate_supers+0x8b/0xd0
[46203.433174]  [<ffffffff8117ad65>] sys_sync+0x45/0x70
[46203.433181]  [<ffffffff8100a0f2>] system_call_fastpath+0x16/0x1b


Seeing that it has something to do with syncing the filesystem, I've tried running 'sync' and it hangs too.  I end up with a similar syslog entry:


Mar  2 08:38:20 tycho kernel: [46443.440537] INFO: task sync:27557 blocked for more than 120 seconds.
Mar  2 08:38:20 tycho kernel: [46443.440539] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Mar  2 08:38:20 tycho kernel: [46443.440541] sync          D 000000010046053b     0 27557  27534 0x00000008
Mar  2 08:38:20 tycho kernel: [46443.440546]  ffff8802a23d9ce8 0000000000000086 ffff880200000000 0000000000015980
Mar  2 08:38:20 tycho kernel: [46443.440550]  ffff8802a23d9fd8 0000000000015980 ffff8802a23d9fd8 ffff880291bd5b80
Mar  2 08:38:20 tycho kernel: [46443.440555]  0000000000015980 0000000000015980 ffff8802a23d9fd8 0000000000015980
Mar  2 08:38:20 tycho kernel: [46443.440559] Call Trace:
Mar  2 08:38:20 tycho kernel: [46443.440562]  [<ffffffff81588c7d>] schedule_timeout+0x22d/0x310
Mar  2 08:38:20 tycho kernel: [46443.440566]  [<ffffffff8104edc2>] ? enqueue_entity+0x132/0x1b0
Mar  2 08:38:20 tycho kernel: [46443.440570]  [<ffffffff8104f283>] ? enqueue_task_fair+0x43/0x90
Mar  2 08:38:20 tycho kernel: [46443.440574]  [<ffffffff81052cf7>] ? enqueue_task+0x77/0x90
Mar  2 08:38:20 tycho kernel: [46443.440577]  [<ffffffff8158885b>] wait_for_common+0xdb/0x180
Mar  2 08:38:20 tycho kernel: [46443.440581]  [<ffffffff81056a00>] ? default_wake_function+0x0/0x20
Mar  2 08:38:20 tycho kernel: [46443.440585]  [<ffffffff815889dd>] wait_for_completion+0x1d/0x20
Mar  2 08:38:20 tycho kernel: [46443.440589]  [<ffffffff81175e73>] writeback_inodes_sb+0xb3/0xe0
Mar  2 08:38:20 tycho kernel: [46443.440592]  [<ffffffff8117acf0>] ? sync_one_sb+0x0/0x30
Mar  2 08:38:20 tycho kernel: [46443.440596]  [<ffffffff8117ac9e>] __sync_filesystem+0x4e/0xa0
Mar  2 08:38:20 tycho kernel: [46443.440599]  [<ffffffff8117ad10>] sync_one_sb+0x20/0x30
Mar  2 08:38:20 tycho kernel: [46443.440602]  [<ffffffff8115550b>] iterate_supers+0x8b/0xd0
Mar  2 08:38:20 tycho kernel: [46443.440605]  [<ffffffff8117ad4f>] sys_sync+0x2f/0x70
Mar  2 08:38:20 tycho kernel: [46443.440609]  [<ffffffff8100a0f2>] system_call_fastpath+0x16/0x1b

A reboot fixes the problem until I do another apt-get upgrade.
Running an fsck returns no problems.  The filesystem is ext4.

I'm debating backing out the latest kernel updates to see if that fixes it.

Any pointers?

---

