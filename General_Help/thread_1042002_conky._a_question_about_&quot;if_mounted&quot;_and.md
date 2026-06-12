---
title: "conky. a question about &quot;if mounted&quot; and checking partitions"
date: 2009-01-17
forum: General Help
---

### Post by ryke on 2009-01-17
Hi,

I've a second hard disk, that is not mounted by default. So, in order to show its disk space only when is mounted, I've set conky with the following:

${if_mounted /media/sdb1ext3}${color #faf779} SDB1EXT3 ${fs_bar 4 /media/sdb1ext3}
${color #faf779}Free: ${fs_free /media/sdb1ext3} | T: ${fs_size /media/sdb1ext3}${alignr}$endif
${if_mounted /media/sdb2ntfs}${color #f3f2bc} SDB2NTFS ${fs_bar 4 /media/sdb2ntfs}
${color #f3f2bc}Free: ${fs_free /media/sdb2ntfs} | T: ${fs_size /media/sdb2ntfs}${alignr}$endif
${if_mounted /media/SDB3FAT32}${color #faf779} SDB3FAT32 ${fs_bar 4 /media/SDB3FAT32}
${color #faf779}Free: ${fs_free /media/SDB3FAT32} | T: ${fs_size /media/SDB3FAT32}${alignr}$endif

Everything is working ok, and disk space is shown only when partitions are mounted.

However, if I run conky from a Terminal, I notice that everytime the following message is displayed:
Conky: statfs '/media/SDB3FAT32': No such file or directory
Conky: statfs '/media/sdb2ntfs': No such file or directory
Conky: statfs '/media/sdb1ext3': No such file or directory

when partitions are not mounted.

Is this normal? Is something wrong in settings?

(I have another "if" for wlan, and no message is displayed when is not up)

Regards

---

