---
title: "Moving WinXP to new disk without reinstalling"
date: 2009-01-22
forum: General Help
---

### Post by doctordruidphd on 2009-01-22
Present situation: Windows XP installed on internal hard drive, with two ntfs paritions: a primary, bootable partition C:, and an extended partition D:. (Why extended, I don't know. That's the way it came)
Ubuntu installed on an external USB drive, ext3,in a primary partition, with swap in an extended partition . System boots with NTLDR loading grub4dos on c: drive (it works).

Desired outcome: Move all of this to a new, much larger internal hard drive. Boot with grub, But most importantly, do this without having to "reinstall" windows. So I need to move C: and D: to larger partitions. Moving Ubuntu is simple; moving windows without reinstalling might not be.

Plan: Copy the windows paritions to the external drive (plenty of room there), remove the old internal drive, install the new one. Set up partitions for windows c: and d:, ubuntu and swap. Oh, and grub would be nice, somewhere along the way.

Not quite sure what the best way is to proceed here. I can move the windows paritions around with dd or partimage, but how do I get them into larger partitions?

Seems there was a HOWTO that covers all this, but I can't find it, now that I need it...

Thanks in advance for comments.

(I don't know how/why this got tagged "gobuntu", but I don't seem to be able to change it)

---

### Post by doctordruidphd on 2009-01-24
I don't know how to make hot links to posts here, but search for:
"Cloned WinXP hard disk freezes on login"
and a posting there explains how to do it.

---

