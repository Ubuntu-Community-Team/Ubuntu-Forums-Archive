---
title: "how to give disk mount/unmount privilege to non-admin user?"
date: 2008-12-03
forum: General Help
---

### Post by asaren on 2008-12-03
Hi,

I tried with Ubuntu 8.10. Non-admin user account doesnt have right to mount/unmount hard drive/partition in computer or flash drive. Only admin user can do this.

So, how to give disk mount/unmount privilege to non-admin user?

Thank you

---

### Post by Fahuadai on 2008-12-03
sudo kate /etc/fstab

add the option 'user' to the disk you want to be user mountable.

for example:

/dev/hda1 /home/myMountPoint ext3 rw,user,auto,exec 0 0

The above sets drive hda, partition 1, to auto mount at the mount point specified/home/myMountPoint using the ext3 file system with the options to read/write enabled, user mountable, automatically mount and allow executables to be run from that partition.

Google /etc/fstab for more info.

Hope this helps.

---

