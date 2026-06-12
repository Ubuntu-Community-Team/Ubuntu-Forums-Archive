---
title: "KLaptop &amp; CPU Throttling"
date: 2005-06-05
forum: Desktop Environments
---

### Post by beefsprocket on 2005-06-05
Right, well I've spent quite some time recompiling and searching for an answer to my problem -- to no avail. Klaptop does not show my CPU speed (1.6Ghz Centrino) at all when clicked. I'm using a custom 2.6.11 kernel. When using the default 2.6.10-5-386 that is bundled with Kubuntu, Klaptop works perfectly. I read somewhere (Fedora?) about root permissions being a potential problem but running as root does not make a difference.

Is there a conflict between cpufreq modules?

DMESG Error:

kernel BUG at kernel/sched.c:2648!
invalid operand: 0000 [#1]
PREEMPT
Modules linked in: speedstep_centrino cpufreq_powersave cpufreq_stats cpufreq_performance cpufreq_ondemand freq_table tg3
CPU:    0
EIP:    0060:[<c0117f25>]    Not tainted VLI
EFLAGS: 00210202   (2.6.11)
EIP is at sub_preempt_count+0x35/0x40
eax: f53f2000   ebx: f53f9c88   ecx: 00000000   edx: 00000001
esi: f53b8e00   edi: 00000000   ebp: f53f2f10   esp: f53f2f10
ds: 007b   es: 007b   ss: 0068
Process gam_server (pid: 3938, threadinfo=f53f2000 task=f53bb0e0)
Stack: 80045102 c02bd8ad f0e58420 f53b8e00 f53b8e00 f53e3e80 08079864 c02bd9ca
       f53b8e00 0000004f 00000004 0000004f f53f2f64 f53f2f68 ffffffe7 f53e3e80
       08079864 c0171b30 f799b20c f53e3e80 80045102 08079864 00000000 f53e3e80
Call Trace:
 [<c02bd8ad>] inotify_ignore+0x5d/0x90
 [<c02bd9ca>] inotify_ioctl+0xea/0xf0
 [<c0171b30>] do_ioctl+0x70/0xa0
 [<c0171d95>] vfs_ioctl+0x65/0x1f0
 [<c0171f65>] sys_ioctl+0x45/0x70
 [<c0103179>] sysenter_past_esp+0x52/0x75
Code: 3b 50 14 89 e5 7f 24 81 fa fe 00 00 00 76 0c b8 00 f0 ff ff 21 e0 29 50 14 5d c3 80 78 14 00 75 ee 0f 0b 5c 0a 6d c5 47 c0 eb e4 <0f> 0b 58 0a 6d c5 47 c0 eb d2 90 55 89 e5 8b 45 08 8b 50 04 89
 ------------[ cut here ]------------
kernel BUG at kernel/sched.c:2648!
invalid operand: 0000 [#2]
PREEMPT
Modules linked in: speedstep_centrino cpufreq_powersave cpufreq_stats cpufreq_performance cpufreq_ondemand freq_table tg3
CPU:    0
EIP:    0060:[<c0117f25>]    Not tainted VLI
EFLAGS: 00210202   (2.6.11)
EIP is at sub_preempt_count+0x35/0x40
eax: f2507000   ebx: f53f9ae8   ecx: 00000000   edx: 00000001
esi: f53b8e00   edi: 00000000   ebp: f2507f10   esp: f2507f10
ds: 007b   es: 007b   ss: 0068
Process gam_server (pid: 4298, threadinfo=f2507000 task=f4124060)
Stack: 80045102 c02bd8ad f0e58594 f53b8e00 f53b8e00 f0cd1080 08078e6c c02bd9ca
       f53b8e00 0000004e 00000004 0000004e f2507f64 f2507f68 ffffffe7 f0cd1080
       08078e6c c0171b30 f799b20c f0cd1080 80045102 08078e6c 00000000 f0cd1080
Call Trace:
 [<c02bd8ad>] inotify_ignore+0x5d/0x90
 [<c02bd9ca>] inotify_ioctl+0xea/0xf0
 [<c0171b30>] do_ioctl+0x70/0xa0
 [<c0171d95>] vfs_ioctl+0x65/0x1f0
 [<c0171f65>] sys_ioctl+0x45/0x70
 [<c0103179>] sysenter_past_esp+0x52/0x75
Code: 3b 50 14 89 e5 7f 24 81 fa fe 00 00 00 76 0c b8 00 f0 ff ff 21 e0 29 50 14 5d c3 80 78 14 00 75 ee 0f 0b 5c 0a 6d c5 47 c0 eb e4 <0f> 0b 58 0a 6d c5 47 c0 eb d2 90 55 89 e5 8b 45 08 8b 50 04 89

---

### Post by brent on 2005-06-05
Is there any reason you are compiling your own kernel?

Are you sure you have right modules selected? Do you have sysfs compiled in?

If you really must compile your own kernel, I suggest you go back to the stock kernel, run lsmod to find out the modules that are loaded. Then in xconfig open the config from the old kernel and remove any modules that aren't needed.

---

