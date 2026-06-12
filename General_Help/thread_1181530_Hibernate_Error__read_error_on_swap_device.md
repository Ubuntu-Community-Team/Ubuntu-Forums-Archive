---
title: "Hibernate Error : read error on swap device"
date: 2009-06-08
forum: General Help
---

### Post by kushal.7 on 2009-06-08
I have ubuntu 9.04. I cant hibernate my system. I just hangs with some lines on screen 
"[some number]read-error on swap device[some number]"
I installed ubuntu through "install inside windows".
pls help.

---

### Post by logos34 on 2009-06-08
can't hibernate/suspend-to-disk (S4) on a Wubi installation, which is what you have

you can still suspend (-to-ram) S3

---

### Post by kushal.7 on 2009-06-08
> **logos34 said:**
> can't hibernate/suspend-to-disk (S4) on a Wubi installation, which is what you have

you can still suspend (-to-ram) S3

means there is no way to hibernate ???...

---

### Post by logos34 on 2009-06-08
no, I don't believe so...it's a known limitation of wubi...basically you're running linux INSIDE windows on a loopback-mounted virtual filesystem...hibernation require a dedicated swap file or partition

---

### Post by stelladeli on 2012-11-28
Hello!
I'm facing the same problem, but I installed Ubuntu 12.10 through CD and "alongside Windows". I didn't use Wubi (at least I think so). And now I am not able to hibernate. Whenever I start the laptop from hibernation ,a whole screen of "read-error on swap-device" appears. Also I distinctly remember that the only partition that is mentioned is /dev/sda5 (ext4) of 366.11 GiB. I do have a /dev/sda6 linux-swap partition of 2 GiB (equal to size of RAM).

I'm quite worried. I recently replaced my hard drive and installed Windows 7 and then Ubuntu 12.10. Is it a problem with the hard drive or the installation???
What should I do? 
Is there a way to fix this?

Thank you very much for your time,effort and consideration in advance!!!

---

### Post by stelladeli on 2013-03-30
If it's any help, my most recent hibernate error (accidentally closed  the laptop lid) showed this screen when I reopened the lid:

[23859.796020] done.
[23859.004491] video LNXVIDEO:01: Restoring backlight state
[23859.005495] Read-error on swap-device (0:0:31000)
[23859.005444] Read-error on swap-device (0:0:31000)
[23859.005440] Read-error on swap-device (0:0:31016)
[23859.005451] Read-error on swap-device (0:0:31024)
[23859.005455] Read-error on swap-device (0:0:31032)
[23859.005450] Read-error on swap-device (0:0:31040)
[23859.060519] Read-error on swap-device (0:0:0904)
[23859.060525] Read-error on swap-device (0:0:0920)
[...many numbers below in the same fashion...I'm also not really sure about the accuracy of the numbers]
[23859.063399] EXT4-fs (sda5): previous I/0 error to superblock detected
[23849.063408] EXT4-fs error (device sda5): ext4_find_entry:1209: inode #12109704L comm kworker/u:53: reading directory lblock 0
[23859.065360] Core dump to |/usr/share/apport/apport 2349 7 0 pipe failed
[23859.069327] Core dump to |/usr/share/apport/apport 3874 7 0 pipe failed
[23859.069430] Core dump to |/usr/share/apport/apport 2160 7 0 pipe failed
[23859.069667] Read-error on swap-device (8:0:23816)
[23859.069676] Read-error on swap-device (8:0:23824)
[numbers] Core dump to |/usr/share/apport/apport 2543 7 0 pipe failed
Core dump to |/usr/apport/apport 2941 7 9 pipe failed
Core dump to |/usr/apport/apport 2568 7 0 pipe failed
Core dump to |/ust/apport/apport 1 7 0 pipe failed
[23859.888708] Kernel panic - not syncing: Attempted to kill init! exitcode=0x00000007
[23850.888708]
[23859.888711] Pid: 1, comm: init Tainted: G            W I  3.5.0.26.generic #42-Ubuntu
[23859.888713] Call Trace:
[23859.888715]  [<c15be940>] panic+0x81/0x17b
[23859.888723]  [<c104ab25>] do_exit+0x745/0x7a0
[23859.888729]  [<c1056872>] ? __sigqueue_free+0x32/0x40
[23859.888732]  [<c104ae24>] do_group_exit+0xa0
[23859.888734]  [<c10591a5>] get_signal_to_deliver+0x175/0x5a0
[23859.888738]  [<c15bdfaa>] ? force_sig_info_fault+0x5a/0x60
[23859.888740]  [<c101091d>] do_signal+0x2d/0x890
[23859.888745]  [<c103e997>] ? kmap_atomic_prot+0xd7/0xf0
[23859.888749]  [<c15be009>] ? is_prefetch.isra.17+0x26/0x130
[23859.888751]  [<c15be7b8>] ? mm_fault_error+0x196/0x1d0
[23859.888754]  [<c15cc0c1>] ? do_page_fault+0x441/0x480
[23859.888759]  [<c114fc28>] ? vfs_write+0xe8/0x160
[23859.888764]  [<c114f070>] ? wait_on_retry_sync_kiocb+0x50/0x50
[23859.888766]  [<c15cbc80>] ? vmailoc_fault+0x176/0x176
[23859.888768]  [<c10113a5>] do_notify_resume+0x85/0xb0
[23859.888770]  [<c15c8c8d>] work_notifysig+0x30/0x37
_



P.S. I apologise for any typos and inaccuracies but the picture from  which I gathered the information didn't have a perfect resolution.


Thank you in advance.

---

### Post by oldos2er on 2013-03-30
Old thread closed. Anyone having further questions, please start a new thread.

---

