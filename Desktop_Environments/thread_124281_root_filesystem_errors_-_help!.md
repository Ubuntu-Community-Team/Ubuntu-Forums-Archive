---
title: "root filesystem errors - help!"
date: 2006-02-01
forum: Desktop Environments
---

### Post by arfon on 2006-02-01
I am running 5.10 and have occasionally been finding that after my machine has been left on for a while the root (/) partition is being marked as 'read only' and I have to reboot.

In an effort to diagnose the problem I have this morning booted from a gentoo boot disk and fsck'd the partition, I have errors left right and centre, the main one being:

Buffer I/O error on dev hda3
hda:dma_intr:status 0x51 {DriveReady SeekComplete Error}
hda:dma_intr:error 0x40 {UncorrectableError}
ide: failed opcode was: unknown


Does this make any sense to anyone?  Is my HD failing?  Any help would be greatly appreciated!

Cheers, arfon

---

### Post by dcstar on 2006-02-01
[QUOTE=arfon]I am running 5.10 and have occasionally been finding that after my machine has been left on for a while the root (/) partition is being marked as 'read only' and I have to reboot.

In an effort to diagnose the problem I have this morning booted from a gentoo boot disk and fsck'd the partition, I have errors left right and centre, the main one being:

Buffer I/O error on dev hda3
hda:dma_intr:status 0x51 {DriveReady SeekComplete Error}
hda:dma_intr:error 0x40 {UncorrectableError}
ide: failed opcode was: unknown

Does this make any sense to anyone?  Is my HD failing?  Any help would be greatly appreciated!

Cheers, arfon[/QUOTE]
It looks like you disk is failing, the sooner you get it replaced the more chance you will have of getting any important data off it.

---

