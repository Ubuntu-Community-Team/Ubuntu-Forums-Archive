---
title: "Ubuntu GRUB Error 18 after fsck failed"
date: 2009-03-08
forum: General Help
---

### Post by bmunger on 2009-03-08
Hello,

I'm having trouble with my email server.

There is no essential data on the machine, but it took me a while to install and I do not want to spend another weekend re-installing...

It first offered me the possibility of going into a maintenance mode to fix it but the fsck there failed to recover the disk. That's when GRUB changed to an Error 18 message.

No way to recover from the Error 18 by itself.

I tried booting from a LiveCD (Ubuntu 8.04.1) and tried running mke2fs -n -S to get the backup superblocks. It ran fine, block size 4096, Superblock backups at 32768, 98304 and so on.

I was able to see the content of the disk with debugfs... so I am still considering it recoverable.

Attempting this command:
sudo fsck -c /dev/sda1

The first pass brought a lot of errors and asked for fixing, I said yes to all of them.

I am running it a second time.

Am I doing the right thing? Any comments?

---

### Post by meierfra. on 2009-03-14
Yes you are doing the right thing. You can make your life a little easier by using "sudo fdisk -yc /dev/sda1"  (then all questions are automatically answered with "yes").

---

