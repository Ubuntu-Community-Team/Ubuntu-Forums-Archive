---
title: "GNOME lockups in ubuntu 9.10"
date: 2010-02-03
forum: Desktop Environments
---

### Post by keithbunt1 on 2010-02-03
I recently built a machine, i3-530, Gigabyte H55M-UD2H with built in graphics. 64-bit install.

I loaded Ubuntu 9.10.  Originally, after logging in, and gnome starting, my pointer would freeze and the machine was unusable.

I found a supposed quick fix that had me replace compiz with metacity inside /etc/xdg/compiz/compiz-manager, on the last line of the config file.  So, COMPIZ_NAME="metacity"

I rebooted and it appeared to fix the problem.

However, now any time the screensaver activates, I have the same problem.

It's not halting or anything, I can still ping it and ssh to it, but the graphics interface is dead.

Any suggestions?  Is this the correct forum?

Thanks

Keith

Here's the stack trace from /var/log/messages

```
Feb  3 22:40:34 newb kernel: [  720.543033] i915/1        D 0000000000000000     0   346      2 0x00000000
Feb  3 22:40:34 newb kernel: [  720.543039]  ffff88010f4fdd70 0000000000000046 0000000000000000 0000000000015880
Feb  3 22:40:34 newb kernel: [  720.543046]  ffff8801116a03b0 0000000000015880 0000000000015880 0000000000015880
Feb  3 22:40:34 newb kernel: [  720.543051]  0000000000015880 ffff8801116a03b0 0000000000015880 0000000000015880
Feb  3 22:40:34 newb kernel: [  720.543057] Call Trace:
Feb  3 22:40:34 newb kernel: [  720.543067]  [<ffffffff81528007>] __mutex_lock_slowpath+0xd7/0x160
Feb  3 22:40:34 newb kernel: [  720.543072]  [<ffffffff81527f06>] mutex_lock+0x26/0x50
Feb  3 22:40:34 newb kernel: [  720.543094]  [<ffffffffa006f8d8>] i915_gem_retire_work_handler+0x38/0x90 [i915]
Feb  3 22:40:34 newb kernel: [  720.543111]  [<ffffffffa006f8a0>] ? i915_gem_retire_work_handler+0x0/0x90 [i915]
Feb  3 22:40:34 newb kernel: [  720.543118]  [<ffffffff810737a5>] run_workqueue+0x95/0x170
Feb  3 22:40:34 newb kernel: [  720.543124]  [<ffffffff81073924>] worker_thread+0xa4/0x120
Feb  3 22:40:34 newb kernel: [  720.543129]  [<ffffffff81078b30>] ? autoremove_wake_function+0x0/0x40
Feb  3 22:40:34 newb kernel: [  720.543135]  [<ffffffff81073880>] ? worker_thread+0x0/0x120
Feb  3 22:40:34 newb kernel: [  720.543140]  [<ffffffff81078746>] kthread+0xa6/0xb0
Feb  3 22:40:34 newb kernel: [  720.543145]  [<ffffffff810130ea>] child_rip+0xa/0x20
Feb  3 22:40:34 newb kernel: [  720.543150]  [<ffffffff810786a0>] ? kthread+0x0/0xb0
Feb  3 22:40:34 newb kernel: [  720.543154]  [<ffffffff810130e0>] ? child_rip+0x0/0x20
Feb  3 22:40:34 newb kernel: [  720.543173] Xorg          D 0000000000000000     0  1372   1370 0x00400004
Feb  3 22:40:34 newb kernel: [  720.543179]  ffff88010a431cb8 0000000000000082 ffff88010a431c90 0000000000015880
Feb  3 22:40:34 newb kernel: [  720.543185]  ffff88010aeade70 0000000000015880 0000000000015880 0000000000015880
Feb  3 22:40:34 newb kernel: [  720.543190]  0000000000015880 ffff88010aeade70 0000000000015880 0000000000015880
Feb  3 22:40:34 newb kernel: [  720.543195] Call Trace:
Feb  3 22:40:34 newb kernel: [  720.543201]  [<ffffffff81528007>] __mutex_lock_slowpath+0xd7/0x160
Feb  3 22:40:34 newb kernel: [  720.543207]  [<ffffffff81428280>] ? sock_aio_write+0x0/0x150
Feb  3 22:40:34 newb kernel: [  720.543212]  [<ffffffff81527f06>] mutex_lock+0x26/0x50
Feb  3 22:40:34 newb kernel: [  720.543228]  [<ffffffffa006fbc6>] i915_gem_throttle_ioctl+0x36/0x90 [i915]
Feb  3 22:40:34 newb kernel: [  720.543250]  [<ffffffffa0035cae>] drm_ioctl+0x17e/0x3a0 [drm]
Feb  3 22:40:34 newb kernel: [  720.543257]  [<ffffffff81036419>] ? default_spin_lock_flags+0x9/0x10
Feb  3 22:40:34 newb kernel: [  720.543262]  [<ffffffff815292ca>] ? _spin_lock_irqsave+0x2a/0x40
Feb  3 22:40:34 newb kernel: [  720.543267]  [<ffffffff8112de5c>] vfs_ioctl+0x7c/0xa0
Feb  3 22:40:34 newb kernel: [  720.543271]  [<ffffffff8112e429>] do_vfs_ioctl+0x79/0x370
Feb  3 22:40:34 newb kernel: [  720.543276]  [<ffffffff8112e7a1>] sys_ioctl+0x81/0xa0
Feb  3 22:40:34 newb kernel: [  720.543281]  [<ffffffff81012002>] system_call_fastpath+0x16/0x1b

```

---

### Post by twista80 on 2010-02-06
I actually have this same exact problem with the same motherboard processor combo. The GNOME locking up on startup only happened to me on my first initial login and after rebooting the issue never resurfaced. However my computer is still freezing up when activating the screensaver too.   

I'm new to Ubuntu. I feel my display is a little choppy too when scrolling through web pages. Would that be something installing drivers would help, and if so does anyone know where I could find them?

---

