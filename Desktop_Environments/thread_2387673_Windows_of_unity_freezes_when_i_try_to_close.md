---
title: "Windows of unity freezes when i try to close"
date: 2018-03-22
forum: Desktop Environments
---

### Post by giobaxx on 2018-03-22
In my ubuntu 14.04 sometimes some windows start to freeze when I try to close them the system starts to become unresponsive. It is also impossible to kill these windows.
In the syslog i found :

```
[72241.260112] INFO: task fsnotify_mark:200 blocked formore than 120 seconds.
``````

[72241.260120]      Tainted: P           OX3.13.0-143-generic #192-Ubuntu
[72241.260123] "echo 0 >/proc/sys/kernel/hung_task_timeout_secs" 
disables this message.
[72241.260127] fsnotify_mark   D ffff88086fcb3b00     0  200      2 
0x00000000
[72241.260135] ffff880856eb7ce0 0000000000000046 ffff880856eb8000
0000000000013b00
[72241.260144] ffff880856eb7fd8 0000000000013b00 ffff880856eb8000
ffff880856eb7e10
[72241.260151]  ffff880856eb7e187fffffffffffffff ffff880856eb8000
0000000000000000
[72241.260158] Call Trace:
[72241.260171] [<ffffffff8173b299>] schedule+0x29/0x70 [72241.260178]  [<ffffffff8173a589>]schedule_timeout+0x279/0x310 [72241.260188] [<ffffffff8101d103>] ? native_sched_clock+0x13/0x80[72241.260194] [<ffffffff8101d179>] ? sched_clock+0x9/0x10 [72241.260201]  [<ffffffff810a2d8d>] ?sched_clock_local+0x1d/0x80 [72241.260208] [<ffffffff8173bdb6>] wait_for_completion+0xa6/0x150[72241.260213]  [<ffffffff810a0410>]? wake_up_state+0x20/0x20 [72241.260221] [<ffffffff810ccd6e>] __synchronize_srcu+0xfe/0x180[72241.260226] [<ffffffff810cc880>] ? call_srcu+0x70/0x70 [72241.260232]  [<ffffffff810cce0d>]synchronize_srcu+0x1d/0x20 [72241.260240] [<ffffffff81209467>] fsnotify_mark_destroy+0x87/0x150[72241.260247] [<ffffffff810b0be0>] ? prepare_to_wait_event+0x100/0x100[72241.260252] [<ffffffff812093e0>] ? fsnotify_put_mark+0x40/0x40[72241.260259] [<ffffffff81090bcb>] kthread+0xcb/0xf0 [72241.260266]  [<ffffffff81090b00>] ?kthread_create_on_node+0x1c0/0x1c0
[72241.260274] [<ffffffff81747e4e>] ret_from_fork+0x6e/0xa0 [72241.260280]  [<ffffffff81090b00>] ?kthread_create_on_node+0x1c0/0x1c0
[72241.260384] INFO: task mel:8754 blocked for more than120 seconds.
[72241.260388]      Tainted: P           OX3.13.0-143-generic #192-Ubuntu
[72241.260390] "echo 0 >/proc/sys/kernel/hung_task_timeout_secs" 
disables this message.
[72241.260393] mel             D ffff88086fc53b00     0 8754   7704 

0x00000004
```

But i really don't know what i can check, or verify if is a problem related of some kernel update or hardware problems....

---

### Post by mörgæs on 2018-03-23
Let's see the hardware. Please copy and paste ```
sudo lshw -sanitize > lshw.txt
``` to the command line, run it and post lshw.txt in CODE tags.

---

### Post by giobaxx on 2018-03-25
tomorrow i will try to look more deeply......but i discovered that user has changed the desktop environment from unity to awesome tha i never used.....:confused:

---

### Post by giobaxx on 2018-03-27
i took a look to that workstation and i logged in using both Desktop Environment*** Unity*** and ***Awesome WM***. i start to think that the problems are the Nvidia Drivers installed on that workstation but i would like to sure.
Sometimes some window freeze (and also the system freeze with unity ) but i'm not able to find anything in the syslog in order to correlate  these malfunctions with the video card, or maybe i don't know where to look....

---

### Post by giobaxx on 2018-04-23
we try to change videocard....but nothing has changed..on a Workstation it happens when I close a window.  Once this problem occurs, I can no longer close any window....

THis is the log, but my linux knolwdge is to  "read" what it say:

```

Apr 19 15:59:58 w1200 kernel: [26041.264142] INFO: task fsnotify_mark:199 blocked for more than 120 seconds.Apr 19 15:59:58 w1200 kernel: [26041.264152]       Tainted: G           OX 3.13.0-144-generic #193-Ubuntu
Apr 19 15:59:58 w1200 kernel: [26041.264155] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Apr 19 15:59:58 w1200 kernel: [26041.264159] fsnotify_mark   D ffff88086fc73b00     0   199      2 0x00000000
Apr 19 15:59:58 w1200 kernel: [26041.264168]  ffff880457209ce0 0000000000000046 ffff880457200000 0000000000013b00
Apr 19 15:59:58 w1200 kernel: [26041.264178]  ffff880457209fd8 0000000000013b00 ffff880457200000 ffff880457209e10
Apr 19 15:59:58 w1200 kernel: [26041.264184]  ffff880457209e18 7fffffffffffffff ffff880457200000 0000000000000000
Apr 19 15:59:58 w1200 kernel: [26041.264192] Call Trace:
Apr 19 15:59:58 w1200 kernel: [26041.264209]  [<ffffffff8173b3e9>] schedule+0x29/0x70
Apr 19 15:59:58 w1200 kernel: [26041.264216]  [<ffffffff8173a6d9>] schedule_timeout+0x279/0x310
Apr 19 15:59:58 w1200 kernel: [26041.264229]  [<ffffffff8109a6e8>] ? update_rq_clock.part.61+0x18/0x40
Apr 19 15:59:58 w1200 kernel: [26041.264241]  [<ffffffff8101d103>] ? native_sched_clock+0x13/0x80
Apr 19 15:59:58 w1200 kernel: [26041.264247]  [<ffffffff8101d179>] ? sched_clock+0x9/0x10
Apr 19 15:59:58 w1200 kernel: [26041.264254]  [<ffffffff810a2d8d>] ? sched_clock_local+0x1d/0x80
Apr 19 15:59:58 w1200 kernel: [26041.264261]  [<ffffffff8173bf06>] wait_for_completion+0xa6/0x150
Apr 19 15:59:58 w1200 kernel: [26041.264267]  [<ffffffff810a0410>] ? wake_up_state+0x20/0x20
Apr 19 15:59:58 w1200 kernel: [26041.264276]  [<ffffffff810ccd6e>] __synchronize_srcu+0xfe/0x180
Apr 19 15:59:58 w1200 kernel: [26041.264282]  [<ffffffff810cc880>] ? call_srcu+0x70/0x70
Apr 19 15:59:58 w1200 kernel: [26041.264288]  [<ffffffff810cce0d>] synchronize_srcu+0x1d/0x20
Apr 19 15:59:58 w1200 kernel: [26041.264298]  [<ffffffff81209467>] fsnotify_mark_destroy+0x87/0x150
Apr 19 15:59:58 w1200 kernel: [26041.264306]  [<ffffffff810b0be0>] ? prepare_to_wait_event+0x100/0x100
Apr 19 15:59:58 w1200 kernel: [26041.264311]  [<ffffffff812093e0>] ? fsnotify_put_mark+0x40/0x40
Apr 19 15:59:58 w1200 kernel: [26041.264321]  [<ffffffff81090bcb>] kthread+0xcb/0xf0
Apr 19 15:59:58 w1200 kernel: [26041.264327]  [<ffffffff81090b00>] ? kthread_create_on_node+0x1c0/0x1c0
Apr 19 15:59:58 w1200 kernel: [26041.264338]  [<ffffffff81747f8e>] ret_from_fork+0x6e/0xa0
Apr 19 15:59:58 w1200 kernel: [26041.264344]  [<ffffffff81090b00>] ? kthread_create_on_node+0x1c0/0x1c0
Apr 19 15:59:58 w1200 kernel: [26041.264512] INFO: task eml:8828 blocked for more than 120 seconds.
Apr 19 15:59:58 w1200 kernel: [26041.264516]       Tainted: G           OX 3.13.0-144-generic #193-Ubuntu
Apr 19 15:59:58 w1200 kernel: [26041.264518] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Apr 19 15:59:58 w1200 kernel: [26041.264521] mel             D ffff88045fd73b00     0  8828   4085 0x00000006
Apr 19 15:59:58 w1200 kernel: [26041.264526]  ffff88040750dac0 0000000000000046 ffff88042ff43000 0000000000013b00
Apr 19 15:59:58 w1200 kernel: [26041.264533]  ffff88040750dfd8 0000000000013b00 ffff88042ff43000 ffff88040750dbf0
Apr 19 15:59:58 w1200 kernel: [26041.264539]  ffff88040750dbf8 7fffffffffffffff ffff88042ff43000 ffff880858a2c160
Apr 19 15:59:58 w1200 kernel: [26041.264546] Call Trace:
Apr 19 15:59:58 w1200 kernel: [26041.264552]  [<ffffffff8173b3e9>] schedule+0x29/0x70
Apr 19 15:59:58 w1200 kernel: [26041.264558]  [<ffffffff8173a6d9>] schedule_timeout+0x279/0x310
Apr 19 15:59:58 w1200 kernel: [26041.264570]  [<ffffffff8107b32e>] ? mod_timer+0x10e/0x230
Apr 19 15:59:58 w1200 kernel: [26041.264576]  [<ffffffff8107b468>] ? add_timer+0x18/0x20
Apr 19 15:59:58 w1200 kernel: [26041.264582]  [<ffffffff8173bf06>] wait_for_completion+0xa6/0x150
Apr 19 15:59:58 w1200 kernel: [26041.264587]  [<ffffffff810a0410>] ? wake_up_state+0x20/0x20
Apr 19 15:59:58 w1200 kernel: [26041.264593]  [<ffffffff810ccd6e>] __synchronize_srcu+0xfe/0x180
Apr 19 15:59:58 w1200 kernel: [26041.264598]  [<ffffffff810cc880>] ? call_srcu+0x70/0x70
Apr 19 15:59:58 w1200 kernel: [26041.264603]  [<ffffffff810cce0d>] synchronize_srcu+0x1d/0x20
Apr 19 15:59:58 w1200 kernel: [26041.264609]  [<ffffffff81208c1e>] fsnotify_destroy_group+0x1e/0x40
Apr 19 15:59:58 w1200 kernel: [26041.264615]  [<ffffffff8120ad22>] inotify_release+0x22/0x50
Apr 19 15:59:58 w1200 kernel: [26041.264622]  [<ffffffff811c6e37>] __fput+0xe7/0x260
Apr 19 15:59:58 w1200 kernel: [26041.264627]  [<ffffffff811c6ffe>] ____fput+0xe/0x10
Apr 19 15:59:58 w1200 kernel: [26041.264633]  [<ffffffff8108d8ef>] task_work_run+0xaf/0xd0
Apr 19 15:59:58 w1200 kernel: [26041.264643]  [<ffffffff8106e700>] do_exit+0x2b0/0xa60
Apr 19 15:59:58 w1200 kernel: [26041.264651]  [<ffffffff811d9600>] ? poll_select_copy_remaining+0x130/0x130
Apr 19 15:59:58 w1200 kernel: [26041.264657]  [<ffffffff8106ef2f>] do_group_exit+0x3f/0xa0
Apr 19 15:59:58 w1200 kernel: [26041.264666]  [<ffffffff8107f580>] get_signal_to_deliver+0x1d0/0x700
Apr 19 15:59:58 w1200 kernel: [26041.264677]  [<ffffffff81014418>] do_signal+0x48/0xa10
Apr 19 15:59:58 w1200 kernel: [26041.264687]  [<ffffffff810d3d6d>] ? ktime_get_ts+0x4d/0xf0
Apr 19 15:59:58 w1200 kernel: [26041.264693]  [<ffffffff81014e49>] do_notify_resume+0x69/0xb0
Apr 19 15:59:58 w1200 kernel: [26041.264701]  [<ffffffff81748470>] int_signal+0x12/0x17
```

---

### Post by giobaxx on 2018-04-23
> [ATTACH]279420[/ATTACH]

In the attachment you can finmd the lshw

---

