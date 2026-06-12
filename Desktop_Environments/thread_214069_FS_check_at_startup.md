---
title: "FS check at startup"
date: 2006-07-12
forum: Desktop Environments
---

### Post by allanlewis on 2006-07-12
Hi,

I have two problems; one is just a niggle and one is really annoying, although I'm not sure if the latter is important or not.

Here they are:

[LIST=1]
[*]When I boot Ubuntu, I get the whole command line spiel instead of a nice progress bar.
[*]During boot, dosfsck is run on my three FAT32 partitions (one is WinXP, one is storage, one is factory-installed recovery partition). Is there any way to stop this and, if so, is it advisable? I ask because it adds significantly to the boot time since the three partitions total about 70GB.
[/LIST]
Thanks in advance!

---

### Post by dolby on 2006-07-12
about no.2 post the content of the /etc/fstab file
i think filesystem check can be bypassed by changing the  0  1 setting of your mounted fat32 partition to 0  0

[this might help a bit more](http://easylinux.info/wiki/Ubuntu_dapper#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

---

### Post by allanlewis on 2006-07-12
> **dolby said:**
> about no.2 post the content of the /etc/fstab file
i think filesystem check can be bypassed by changing the  0  1 setting of your mounted fat32 partition to 0  0

[this might help a bit more](http://easylinux.info/wiki/Ubuntu_dapper#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

Thanks! I love it when solutions are so simple :)

UPDATE: Actually, this solution isn't working! The Linux FS is only checked every so many boots, but my FAT32 partitions are still being checked on every boot! Any other ideas?

---

