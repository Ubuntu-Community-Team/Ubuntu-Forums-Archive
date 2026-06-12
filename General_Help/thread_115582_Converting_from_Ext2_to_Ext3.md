---
title: "Converting from Ext2 to Ext3"
date: 2006-01-10
forum: General Help
---

### Post by ronmarley1 on 2006-01-10
When I first set up Ubuntu, I formatted the drive as Ext2 (it's what PartitionMagic suggested). Should I convert my Ext2 file system to Ext3? If it's a difficult process, is it worth it? I'd hate to mess up what I have now (smooth running Windows free PC).
Thanks in advance...
PS, I originally posted this in the Desktop Support forum at [http://www.ubuntuforums.org/showthread.php?t=115574](http://www.ubuntuforums.org/showthread.php?t=115574)
Could a moderator please delete that post?
Thanks, and sorry

---

### Post by o_fortuna on 2006-01-10
[QUOTE=ronmarley1]When I first set up Ubuntu, I formatted the drive as Ext2 (it's what PartitionMagic suggested). Should I convert my Ext2 file system to Ext3? If it's a difficult process, is it worth it? I'd hate to mess up what I have now (smooth running Windows free PC).
Thanks in advance...
PS, I originally posted this in the Desktop Support forum at [http://www.ubuntuforums.org/showthread.php?t=115574](http://www.ubuntuforums.org/showthread.php?t=115574)
Could a moderator please delete that post?
Thanks, and sorry[/QUOTE]
There's really no huge reason to convert to ext3, but gparted (under Applications --> System Tools) should be able to reformat it (you might have to unmount it?). If it were me, I wouldn't go through the trouble, though. Ext2 lacks a few 'features,' but the difference isn't huge.

---

### Post by BoyOfDestiny on 2006-01-10
[QUOTE=o_fortuna]There's really no huge reason to convert to ext3, but gparted (under Applications --> System Tools) should be able to reformat it (you might have to unmount it?). If it were me, I wouldn't go through the trouble, though. Ext2 lacks a few 'features,' but the difference isn't huge.[/QUOTE]

I'll mention 1. Fragmentation. ext3 reduces it (big time). I'd recommend formatting just for this reason.

I checked wikipedia, from [http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)

"it does have the significant advantage in that it allows in-place upgrades from the popular ext2 file system without having to backup and restore data."

So I guess google for how to convert from ext2 to ext3, incase gparted doesn't handle it without reformatting completely (I honestly have no idea, since I'm using reiserfs)

---

### Post by ronmarley1 on 2006-01-10
Thank you for the replies.

---

### Post by RikoW on 2006-01-11
Hi,

the ext3 filesystem (at least in my simple mind) has the BIG advantage that the system boots much faster after an un-controlled shutdown (e.g. after system freeze, power failure etc), because a full filesystem check does not have to be performed after not un-mounting the filesystem cleanly.

However, converting an ext2 to ext3 is as simple as 1-2-3 by using the command tune2fs (check the man page).

You probably want to un-mount the partition which you want to convert - the safest way is therefore to boot your machine with a live-cd.

After that you just need to do:
> tune2fs -j /dev/hda7    # substitute 7 to whatever the desired partition is

This adds a journal to ext2 making it an ext3.

Remember also to adjust the filesystem type in /etc/fstab. I did it myself a couple of times in the past and it always worked.

Cheers,

             Riko

---

