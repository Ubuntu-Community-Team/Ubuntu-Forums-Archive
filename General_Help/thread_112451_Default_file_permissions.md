---
title: "Default file permissions"
date: 2006-01-04
forum: General Help
---

### Post by sandisn on 2006-01-04
Hello!

I'm sharing my computer with my brother. The problem is - we need a shared folder where we both can write (delete). For example if he drops some photos in there for me to modify i would like to do that without "sudo chmod ...". Now I have set up "shared-files" partition and mounted it at /media/shared-files . Is there a way to automatically chmod every file and folder that appears on that partition to 777?

Or perhaps there is other solutions to this "local file sharing" problem?
Thanks in advance.

---

### Post by oakz on 2006-01-04
If you format the partition as vfat you can set the default umask for the partition in /etc/fstab by adding the following line (replacing /dev/hda6 as appropriate):

/dev/hda6       /media/shared-files      vfat    umask=000        0       0

All files created in shared-files will be with file permissions 777.

See the mount manpage for all filesystems that support setting the umask in this way. (I don't think you can do this with ext2/3 filesystems)

Alternatively you can set the default umask in /etc/profile or ~/.bash_profile , but beware that this will affect all file creations, not just the ones in your shared partition.

---

