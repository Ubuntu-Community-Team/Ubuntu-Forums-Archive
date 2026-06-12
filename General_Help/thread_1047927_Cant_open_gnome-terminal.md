---
title: "Cant open gnome-terminal"
date: 2009-01-22
forum: General Help
---

### Post by ju2wheels on 2009-01-22
This is really random and Im at a loss here. All I was doing was browsing the web and had one terminal open doing nothing. The terminal then said it stopped responding so I closed it and thought nothing of it and now I cant open a terminal.

I get the following error in my logs:
```

Jan 22 22:40:41 efgefg kernel: [343238.478111] Inbound IN=eth0 OUT= MAC=00:0b:29:8e:13:a8:00:07:84:a3:f5:40:08:00 SRC=190.152.23.86 DST=128.113.192.227 LEN=56 TOS=0x00 PREC=0x00 TTL=37 ID=3982 PROTO=ICMP TYPE=3 CODE=3 [SRC=128.113.192.227 DST=190.152.23.86 LEN=44 TOS=0x00 PREC=0x00 TTL=40 ID=12346 DF PROTO=TCP INCOMPLETE [8 bytes] ] 
Jan 22 22:41:30 efgefg kernel: [343287.076139] INFO: task gnome-terminal:24318 blocked for more than 120 seconds.
Jan 22 22:41:30 efgefg kernel: [343287.076149] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 22 22:41:30 efgefg kernel: [343287.076151] gnome-termina D ffffffff80234059     0 24318      1
Jan 22 22:41:30 efgefg kernel: [343287.076155]  ffff8800018fbbc8 0000000000000082 ffff8800818fbd57 ffff8800018fbc78
Jan 22 22:41:30 efgefg kernel: [343287.076159]  ffffffff807a5400 ffffffff807a5400 ffffffff807a5400 ffffffff807a5400
Jan 22 22:41:30 efgefg kernel: [343287.076162]  ffffffff807a5400 ffffffff807a5400 ffffffff807a5400 ffffffff807a5400
Jan 22 22:41:30 efgefg kernel: [343287.076165] Call Trace:
Jan 22 22:41:30 efgefg kernel: [343287.076171]  [<ffffffff80500e55>] schedule_timeout+0x95/0xd0
Jan 22 22:41:30 efgefg kernel: [343287.076174]  [<ffffffff80500c06>] wait_for_common+0xb6/0x1a0
Jan 22 22:41:30 efgefg kernel: [343287.076178]  [<ffffffff802475b0>] ? default_wake_function+0x0/0x10
Jan 22 22:41:30 efgefg kernel: [343287.076181]  [<ffffffff80500d88>] wait_for_completion+0x18/0x20
Jan 22 22:41:30 efgefg kernel: [343287.076185]  [<ffffffff80262cc2>] flush_cpu_workqueue+0x62/0xa0
Jan 22 22:41:30 efgefg kernel: [343287.076188]  [<ffffffff80262920>] ? wq_barrier_func+0x0/0x20
Jan 22 22:41:30 efgefg kernel: [343287.076190]  [<ffffffff80262e53>] flush_workqueue+0x53/0x70
Jan 22 22:41:30 efgefg kernel: [343287.076192]  [<ffffffff80262e85>] flush_scheduled_work+0x15/0x20
Jan 22 22:41:30 efgefg kernel: [343287.076196]  [<ffffffff8040b75d>] tty_ldisc_release+0x4d/0x1f0
Jan 22 22:41:30 efgefg kernel: [343287.076198]  [<ffffffff8050263e>] ? _spin_lock+0xe/0x20
Jan 22 22:41:30 efgefg kernel: [343287.076201]  [<ffffffff804051cd>] release_dev+0x45d/0x5c0
Jan 22 22:41:30 efgefg kernel: [343287.076205]  [<ffffffff802fc281>] ? locks_remove_posix+0x11/0xc0
Jan 22 22:41:30 efgefg kernel: [343287.076208]  [<ffffffff8031fa56>] ? inotify_inode_queue_event+0x16/0x100
Jan 22 22:41:30 efgefg kernel: [343287.076210]  [<ffffffff8040534e>] tty_release+0x1e/0x30
Jan 22 22:41:30 efgefg kernel: [343287.076213]  [<ffffffff802eafa9>] __fput+0xc9/0x1b0
Jan 22 22:41:30 efgefg kernel: [343287.076215]  [<ffffffff802eb0b5>] fput+0x25/0x30
Jan 22 22:41:30 efgefg kernel: [343287.076217]  [<ffffffff802e744b>] filp_close+0x5b/0x90
Jan 22 22:41:30 efgefg kernel: [343287.076220]  [<ffffffff802e753f>] sys_close+0xbf/0x120
Jan 22 22:41:30 efgefg kernel: [343287.076223]  [<ffffffff8021285a>] system_call_fastpath+0x16/0x1b

```

---

### Post by mssever on 2009-01-22
What error messages (if any) do you get when starting gnome-terminal from a terminal?

(You can hit <Alt>F2 and type "xterm" to get a basic terminal you can use for answering this question.)

---

### Post by ju2wheels on 2009-01-22
I used ALT+F2 to forward ps output to a file on my desktop and found a gnome-terminal process running in the background and killed it. It then allowed me to spawn a new gnome-terminal.

The issue I have now is that my process list is showing multiple gnome-terminals running when I truly only have one open and nothing I do is able to terminate them.
 Ive used killall and kill -9 with the PID and even tried with sudo as well but none seems to terminate the extra processes.

Heres what I have now:
```

$ ps aux | grep terminal
1000       792  2.1  0.7 301188 31416 ?        Sl   23:22   0:00 gnome-terminal
1000     24318  0.0  0.7 296408 30348 ?        D    22:16   0:00 gnome-terminal
1000     29361  0.0  0.0      0     0 ?        D    22:54   0:00 [gnome-terminal]
1000     30216  0.0  0.7 300924 31124 ?        D    22:59   0:00 gnome-terminal
1000     31552  0.0  0.0      0     0 ?        D    23:09   0:00 [gnome-terminal]

```

---

### Post by mssever on 2009-01-22
> **ju2wheels said:**
> The issue I have now is that my process list is showing multiple gnome-terminals running when I truly only have one open and nothing I do is able to terminate them.
 Ive used killall and kill -9 with the PID and even tried with sudo as well but none seems to terminate the extra processes.

If you look at htop (or even regular top), you'll likely discover that those processes are zombies. If so, they can't be killed aside from a reboot.

---

