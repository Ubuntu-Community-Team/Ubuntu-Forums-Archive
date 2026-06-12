---
title: "KDE Crashes/Restarts Arbitrarily"
date: 2008-03-30
forum: Desktop Environments
---

### Post by PieSquared on 2008-03-30
Lately I've been having a problem with KDE (3.5.9, I think...) arbitrarily crashing and then restarting (going back to the login screen). I don't exactly know when this started, and I dont remember installing anything that could cause it, nor can I determine a set behaviour which triggers it.

Having no idea what is going on, I tried dmesg. It gave me the following (I've only included things which seem like they could possibly be errors, and dmesg | tail doesn't have any ERRORS in it, I think.)

```

...
[   57.348545] Bluetooth: HCI device and connection manager initialized
[   57.348549] Bluetooth: HCI socket layer initialized
[   57.362015] Bluetooth: L2CAP ver 2.8
[   57.362021] Bluetooth: L2CAP socket layer initialized
[   57.449438] Bluetooth: RFCOMM socket layer initialized
[   57.449560] Bluetooth: RFCOMM TTY layer initialized
[   57.449563] Bluetooth: RFCOMM ver 1.8
[B][  121.591394] nvidia: module license 'NVIDIA' taints kernel.
[  121.851009] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[  121.851713] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9639  Mon Apr 16 20:20:06 PDT 2007[/B]
[  121.922804] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[  121.923150] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode

...
[B][338129.074874] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/fs/inotify.c:172 set_dentry_child_flags()
[338129.074907]  [<c0191bad>] set_dentry_child_flags+0xcd/0x130
[338129.074941]  [<c0191c63>] remove_watch_no_event+0x53/0x60
[338129.074951]  [<c0191d88>] inotify_remove_watch_locked+0x18/0x50
[338129.074955]  [<c016b085>] vfs_read+0x125/0x160
[338129.074972]  [<c019209c>] inotify_rm_wd+0x6c/0xb0
[338129.074988]  [<c01925d8>] sys_inotify_rm_watch+0x38/0x60
[338129.074999]  [<c0103f62>] sysenter_past_esp+0x6b/0xa9[/B]


...

```

The first part seems to be something withthe NVIDIA drivers... I've had problems with them before, but I thought I fixed them, and everything seems to be working fine. Ideas?

The second part - I don't know what it is. But it looks like an error message. And those few lines are repeated many times over and over.

As you can see, I'm pretty much clueless and have no idea how to go about fixing this or even diagnosing a problem. Advice, suggestions, comments, etc are welcome. Thanks.

PS. I'm not actually sure it's a problem with KDE. It's just that I also use GNOME and I don't remember this ever happening in GNOME. I'm using Ubuntu Gutsy.

---

