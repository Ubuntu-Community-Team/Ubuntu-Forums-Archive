---
title: "KDE locks"
date: 2005-03-21
forum: Desktop Environments
---

### Post by accensi on 2005-03-21
I am running Hoary with kernel 2.6.11-1, and almost everything is working ok.

Since I installed KDE 3.4 and returned to use some KDE applications, i am getting systems locks only recovered by poweroff or hard reset.

In the logs there is a lot of entries like:
kernel: scheduling while atomic: gam_server/0xffffffff/9019
kernel: [<c0268eea>] schedule+0x40/0x42f
kernel: [<c012f45e>] __get_free_pages+0x18/0x31
kernel: [<c0269ace>] schedule_timeout+0x7e/0x99
kernel: [<c011c028>] process_timeout+0x0/0x5
kernel: [<c0152bb5>] do_poll+0x8d/0xab
kernel: [<c0152cf0>] sys_poll+0x11d/0x1b9
kernel: [<c01522b1>] __pollwait+0x0/0x94
kernel: [<c0118529>] sys_gettimeofday+0x25/0x55
kernel: [<c0102a3d>] sysenter_past_esp+0x52/0x75

These errors are reported from some time with an issue of gamin with KDE use of FAM, as int this kernel threads and gamin mailing lists (and other places)

Gamin version is gamin (0.0.26-0ubuntu1.

Any one is also getting this bug?

There is a workaround or correction?

Thanks

A. C. Censi

---

### Post by s3verian on 2005-04-05
It's a (resolved) bug.  
[https://bugzilla.ubuntu.com/show_bug.cgi?id=7346](https://bugzilla.ubuntu.com/show_bug.cgi?id=7346)

The workaround was to add the **noinotify** switch to the kernel in /boot/grub/menu.lst

title           Ubuntu, kernel 2.6.11-1-k7
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.11-1-k7 root=/dev/hda2 ro quiet splash vga=792 **noinotify**
initrd          /boot/initrd.img-2.6.11-1-k7
savedefault
boot

---

### Post by pjkundert on 2005-08-08
This bug is not resolved.   I ran into it installing on a machine yesterday, and here is how I worked around it.

For me, this bug appeared to be an interaction between the kernel CONFIG_PREEMT and the NVidia driver (both X.org 'nv' and NVidia's 'nvidia' drivers causes the problem to appear, with the kernel CONFIG_PREEMT configuration enabled).

A few seconds (at most, a minute or so) after logging in, using either KDE or Gnome, the machine would lock up.  I was able to catch it a couple of times (by switching to the console just before lockup, or viewing the logs if I was lucky enough for them to flush before the machine hung hard), and I saw the scheduling while atomic: gam_server/... message.

I installed every available kernel from 2.6.9 to 2.6.12, and used both the nv and nvidia drivers, and the results were virtually identical.  Sometimes a hard lock, sometimes (I suspect), just the X.org driver locked up.  However, since I didn't have a proper network switch at the site, I couldn't log into the machine via SSH to be certain...)

SOLUTION

I recompiled the 2.6.11 kernel with CONFIG_PREEMPT (and CONFIG_PREEMT_BKL) turned OFF.  This resolved the "hard lock" issue, but the X.org 'nv' driver still caused problems (the Xorg X server hung up after a while).  I compiled and installed the 'nvidia' driver, and everything works now.

RECOMMENDATION

The CONFIG_PREEMPT and/or CONFIG_PREEMPT_BKL kernel code is causing problems, OR both the 'nv' AND the 'nvidia' drivers are defective.  Since the X.org 'nv' driver is entirely in user space (I think...  perhaps there are kernel-space AGP resource modules that are used?), I suspect that the "scheduling while atomic:..." problem is primarily caused by the CONFIG_PREEMPT or CONFIG_PREEMPT_BKL kernel code.

Therefore, the Ubuntu kernels should disable CONFIG_PREEMPT and CONFIG_PREEMPT_BKL until the kernel defect is resolved.  I did not attempt to recompile with JUST the CONFIG_PREEMPT_BKL disabled; if someone else is running into this issue, and wants to help isolate the problem further, this might be an interesting test.

Also, I would recomment that the Ubuntu project (somehow) ship NVidia's 'nvidia' driver.  I know that there are licensing issues, but the 'nv' driver seems to be broken, regardless of the state of the kernel CONFIG_PREEMPT.

---

