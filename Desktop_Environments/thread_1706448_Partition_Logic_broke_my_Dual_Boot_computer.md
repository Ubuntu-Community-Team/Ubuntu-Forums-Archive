---
title: "Partition Logic broke my Dual Boot computer"
date: 2011-03-13
forum: Desktop Environments
---

### Post by samm10 on 2011-03-13
I used Partition Logic to expand Ubunto and Vista partitions.  It failed miserably.

Now I trying to use GParted but it only lists the following:

[LIST]
[*]GParted
[INDENT]Devices[/INDENT]
[INDENT][INDENT]/dev/sda  931.51 GiB [/INDENT][/INDENT]
[/LIST]


Partition       File System  Size      Used    Unused   Flags
unallocated !   unallocated  931.51 GiB   ---     ---

---

### Post by wilee-nilee on 2011-03-13
> **samm10 said:**
> I used Partition Logic to expand Ubunto and Vista partitions.  It failed miserably.

Now I trying to use GParted but it only lists the following:

[LIST]
[*]GParted
[INDENT]Devices[/INDENT]
[INDENT][INDENT]/dev/sda  931.51 GiB [/INDENT][/INDENT]
[/LIST]


Partition       File System  Size      Used    Unused   Flags
unallocated !   unallocated  931.51 GiB   ---     ---

First don't boot into your install and boot a live cd and take a screen shot of gparted, and post it. Stay off the HD and only use the live cd as of now, if there is any chance of recovery, if that is needed, the HD needs to not be written to any more.

Also let us know what you have as far as any recovery stuff for vista. For example do you have a recovery disc, and or do you have a image or backup of the whole thing?

---

