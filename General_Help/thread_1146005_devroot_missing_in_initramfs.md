---
title: "/dev/root missing in initramfs"
date: 2009-05-02
forum: General Help
---

### Post by the.ruediger on 2009-05-02
Hello,

I installed a fresh copy of Ubuntu 9.04 Jaunty with a software RAID and LVM (alt installer). But somehow the initramdisk wasn't created properly. When I try to boot I get an error message that /dev/root is missing and that the boot process gave up waiting for the root partition to get mounted and I end up in a busybox shell prompt.

Manually linking /dev/mapper/vg1-root--lv (my root partition/logical volume) to /dev/root and exiting the busybox shell fixes the problem.

But it's quite annoying to type it in every time I boot my machine (despite the fact that this is probably the best way to secure your system against non-nerds ;)) I want to fix it for good. How can I repair my initramdisk to create the link on its own?

---

### Post by mkrahmeh on 2009-05-02
sorry if am not familiar with initramdisk, but have you considered placing the link command in one of the rc.d's ? or is it that these scripts do not work unless the boot goes right ?

there must be somewhere to place the command in (one of the startup scripts)

---

### Post by unutbu on 2009-05-02
I don't know anything about RAID, so please forgive me if this is just plain wrong. 

What happens if you edit /etc/fstab, changing /dev/root to /dev/mapper/vg1-root--lv ?

---

### Post by the.ruediger on 2009-05-03
What a surprise. Setting the right root= parameter in /boot/grub/menu.lst worked :). It was set to the UUID and not /dev/mapper/vg1-root--lv

---

### Post by _2009 on 2009-08-06
I'm having this issue intermittently on Ubuntu Server but we're using LILO.

I'm very new to Linux/Ubuntu and have no idea how to fix this from the busy box shell.

The server used to boot 1 time out of 10 but now the won't seem to boot at all.

All suggestions welcome.

Many Thanks,
_2009

---

