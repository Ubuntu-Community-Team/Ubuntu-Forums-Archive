---
title: "Help with clean re-install of dual-boot system"
date: 2009-01-28
forum: General Help
---

### Post by waldrepdebater on 2009-01-28
I am currently dual-booting ubuntu 8.10 with windows vista on my Acer aspire laptop.  I have done some research on Windows 7 beta and I would like to upgrade vista to it.  My hard drive has gotten pretty cluttered over the last two years and this seems like a good opportunity to organize it.  I would like to run my plan by you all and get some feedback.  I also have a few questions at the end.

My plan:

1. Backup any files I need on either OS

2. Wipe the HD

3. Install Windows 7 beta

4. Shrink the Windows partition and install Ubuntu 8.10 on a new partition.

Questions:

The laptop came with some pre-installed Acer software on Vista, tools for projector compatibility, internet config, etc.  Will I need this to run Windows 7 on the laptop easily?  If so, what should I do?  (I realize this is probably not the best place to ask this...)

What is the best way to wipe my entire HD at once?  I thought about running rm -rf / in terminal, but wouldn't that just delete the main linux partition and leave the windows and swap partitions?

My current partition setup is kinda haphazard.  If I am going to re-format the HD I want to do it right and end up with the best setup possible.  Here is my current config:  (output of sudo fdisk -l)
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         892     7164958+  27  Unknown
/dev/sda2   *         893        5193    34546671    7  HPFS/NTFS
/dev/sda3            8411       12044    29184947+   7  HPFS/NTFS
/dev/sda4            5194        8410    25840552+   5  Extended
/dev/sda5   *        5194        8271    24724003+  83  Linux
/dev/sda6            8272        8410     1116486   82  Linux swap / Solaris
``` I have heard friends talk about separate partitions for GRUB, a separate home directory, and all kinds of other partition formats.  In your opinion, what would be the best setup for dual-booting ubuntu newbie, and how would I set it up if it is different from my current system?

Any other advice?

---

