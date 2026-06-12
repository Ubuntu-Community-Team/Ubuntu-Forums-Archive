---
title: "Boot Problems"
date: 2006-09-25
forum: Desktop Environments
---

### Post by Star Solutions on 2006-09-25
I installed the Server CD installation on my Dell Pentium(1) 200Mhz with 64MB of RAM. The installtion worked fine and completed without any problems. I then went to start the computer. I got the GRUB launcher and it gets past that. Ubuntu begins to start but fails as soon as it displays "boot" on the screen. Then the system instantly restarts with no explanation.

Any ideas why it won't start?

---

### Post by Gotterdammerung on 2006-09-25
Which error messages to you see? During boot, try pressing I for step-by-step initialization. If all fails, try booting with Ubuntu LiveCD and:

1) Lets suppose you have installed Ubuntu on /dev/hda1
$ mount /dev/hda1 /mnt/hda1
$ mount -o bind /dev /mnt/hda1/dev
$ mount -o bind /proc /mnt/hda1/proc
$ chroot /mnt/hda1 /bin/bash
$ source /etc/profile
$ dmesg > erros.txt

2) Post erros.txt here, so we can evaluate your problem.

---

