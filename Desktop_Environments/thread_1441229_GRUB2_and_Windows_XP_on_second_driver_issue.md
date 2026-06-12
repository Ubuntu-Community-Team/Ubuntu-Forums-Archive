---
title: "GRUB2 and Windows XP on second driver issue"
date: 2010-03-28
forum: Desktop Environments
---

### Post by rafitrus on 2010-03-28
Hi. I am new to Ubuntu environment but I do know a little bit. I have tried installing ubuntu 10.04 and windows xp on two hard drives. First time, xp was master and ubuntu slave which did not work out. Then I tried otherwise, and I did. Now I have Ubuntu 10.04 on my master driver and XP on my slave but... I can't make XP bootable. I have tried adding it directly to grub.cfg and running update-grub. In first case, XP never showed up while booting, and in the other case I keep getting error that there is no such device.

this is my entry in grub.cfg responsible for booting XP

### BEGIN /etc/grub.d/30_os-prober ###

menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
        set root=(hd1,1)
        chainloader +1

### END /etc/grub.d/30_os-prober ##


I need help, I appreciate it...

---

