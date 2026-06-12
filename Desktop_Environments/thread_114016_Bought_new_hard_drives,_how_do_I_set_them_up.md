---
title: "Bought new hard drives, how do I set them up?"
date: 2006-01-07
forum: Desktop Environments
---

### Post by ardchoille on 2006-01-07
I bought two new 80Gb hard drives and am in need of the following:

1. How do I format them for use with Linux? Does this depend on the distro I am using?

2. How do I set them up so that they are both mounted when the system boots?

3. Is there anything else I need to do to have these two hard drives ready for use when I log in?

---

### Post by patrickfromspain on 2006-01-07
yo can install gparted and format them from there.

---

### Post by dcstar on 2006-01-07
[QUOTE=ardchoille]I bought two new 80Gb hard drives and am in need of the following:

1. How do I format them for use with Linux? Does this depend on the distro I am using?

2. How do I set them up so that they are both mounted when the system boots?

3. Is there anything else I need to do to have these two hard drives ready for use when I log in?[/QUOTE]
If you are adding them to an existing Ubuntu install, then keep this in mind:

The Master device on the first IDE channel Ubuntu finds will be designated hda, the Slave device on that channel hdb. For the second IDE channel, it is hdc and hdd.

Once you use something like gparted to put filesystems on, then you can manually edit your /etc/fstab file to make sure they are mounted on boot-up (if they aren't there already).

System-Administration-Disks also allows you to see the disks.

---

### Post by ardchoille on 2006-01-07
[QUOTE=dcstar]If you are adding them to an existing Ubuntu install, then keep this in mind:

The Master device on the first IDE channel Ubuntu finds will be designated hda, the Slave device on that channel hdb. For the second IDE channel, it is hdc and hdd.

Once you use something like gparted to put filesystems on, then you can manually edit your /etc/fstab file to make sure they are mounted on boot-up (if they aren't there already).

System-Administration-Disks also allows you to see the disks.[/QUOTE]
Wow, thank you very much for this great info. You are appreciated :)

---

