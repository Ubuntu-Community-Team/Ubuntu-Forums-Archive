---
title: "Boot problem! MAy day! May day! (In April)"
date: 2006-04-21
forum: Desktop Environments
---

### Post by gman2004 on 2006-04-21
OK!
After Grub loads, I select ubuntu, the system hungs for while and then this is the error message I get:> [4294738.135000] EXT3-fs error (device hdb2 ext3_check_descriptors: Inode bitmap for group 384 not in group (block 2147483647)! 
[4294738.136000] EXT3-gs: group descriptors corrupted!
BusyBox v1.00-pre10 (Debian 20040623-1 ubuntu22) Built-in shell (ash)
/bin/sh: can't access tty; job control turned off
#


Any clues?

---

### Post by joft on 2006-04-22
Hi,

well it seems like your partition called /dev/hdb2 is corrupt and needs do be fsck'd . Is it your root partition? I'm not sure if fsck is available in the console you are showing above, but you could try:
```
fsck -f /dev/hdb2
```

---

