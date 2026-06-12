---
title: "Partimage help?"
date: 2009-05-04
forum: General Help
---

### Post by crispeto on 2009-05-04
I've tried following all instructions but I'm ready to pull my hair out (what little there is left:). Here's what I try and do once I'm in Partimage:
1.  Under "Partition to save/restore" I choose my Ubuntu HD titled sda1.
2.  "Image file to create/use" I call it /backup/sda1
3.  "Action to be done" I choose "save partition into a new image file"
4.   When I hit F5 I get "The /dev/sda1 partition is mounted. Partition Image can't work on mounted partitions. Please, unmount it before.  You can do it with "umount /" It includes two red boxes either "continue" or "Cancel"

Here's where I'm lost. Is it telling me to unmount my HD or the drive where I'm trying to backup the HD to. If I'm supposed to unmount the HD, how do I do that? Bottom line: what do I do from here? Thanks much!

---

### Post by dcstar on 2009-05-05
> **crispeto said:**
> I've tried following all instructions but I'm ready to pull my hair out (what little there is left:). Here's what I try and do once I'm in Partimage:
1.  Under "Partition to save/restore" I choose my Ubuntu HD titled sda1.
2.  "Image file to create/use" I call it /backup/sda1
3.  "Action to be done" I choose "save partition into a new image file"
4.   When I hit F5 I get "The /dev/sda1 partition is mounted. Partition Image can't work on mounted partitions. Please, unmount it before.  You can do it with "umount /" It includes two red boxes either "continue" or "Cancel"

Here's where I'm lost. Is it telling me to unmount my HD or the drive where I'm trying to backup the HD to. If I'm supposed to unmount the HD, how do I do that? Bottom line: what do I do from here? Thanks much!

You cannot copy in use (mounted) partitions which you run the actual system off, boot off a Live CD and do it with that.

---

