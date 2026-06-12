---
title: "Live image backup of the whole hard-drive?"
date: 2009-02-12
forum: General Help
---

### Post by andreit on 2009-02-12
I would like to make a sector by sector image of my hard-drive and store it on a secondary hard-drive. Acronis True Image does this on Windows, and it does it while the OS is running. If my laptop hard-drive fails, I want to be able to boot off a USB stick or CD, pop a new hard-drive into the laptop and restore the backup image.

How can I do that on Linux?

---

### Post by dcstar on 2009-02-12
> **andreit said:**
> I would like to make a sector by sector image of my hard-drive and store it on a secondary hard-drive. Acronis True Image does this on Windows, and it does it while the OS is running. If my laptop hard-drive fails, I want to be able to boot off a USB stick or CD, pop a new hard-drive into the laptop and restore the backup image.

How can I do that on Linux?

```
man dd
```

Or use the partition copy in the Partition Editor.

---

### Post by andreit on 2009-02-12
> **dcstar said:**
> ```
man dd
```

Or use the partition copy in the Partition Editor.

Thank you for your reply.

The backup needs to be
- incremental
- live
- backup the / filesystem while it's mounted

dd does none of this..

---

### Post by JECHO on 2009-02-12
> **andreit said:**
> Thank you for your reply.

The backup needs to be
- incremental
- live
- backup the / filesystem while it's mounted

dd does none of this..


I just made the exact same post a few weeks ago... here is a solution for you... a command line utility called remastersys.

look here: [http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

---

### Post by andreit on 2009-02-12
> **JECHO said:**
> I just made the exact same post a few weeks ago... here is a solution for you... a command line utility called remastersys.

look here: [http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

Thanks.

Hopefully it would make its way into the main repository.

---

### Post by dcstar on 2009-02-12
> **andreit said:**
> Thank you for your reply.

The backup needs to be
- incremental
- live
- backup the / filesystem while it's mounted

dd does none of this..

It does a "sector by sector image" as **you** specifically requested. BTW, I have dd currently currently backing up my **mounted** root filesystem.

Programs that back up in the way you want are usually commercial and expensive, as they have to make a "snapshot" of a running system and then copy that while the system continues to run and modify itself.

The easiest thing for you would be to create a RAID-1 array so the drive is truly mirrored at all times.

---

### Post by nxmehta on 2009-06-19
> **dcstar said:**
> It does a "sector by sector image" as **you** specifically requested. BTW, I have dd currently currently backing up my **mounted** root filesystem.

Programs that back up in the way you want are usually commercial and expensive, as they have to make a "snapshot" of a running system and then copy that while the system continues to run and modify itself.

The easiest thing for you would be to create a RAID-1 array so the drive is truly mirrored at all times.

If you're backing up a mounted root filesystem with dd, good freaking luck, because you're going to get some filesystem corruption.  Ever tried restoring those backups?

Also, RAID IS NOT A BACKUP SOLUTION.  I'm not going to explain all the problems with using RAID for backup- you can just google it.

The OP had a very good question which you seem to have missed the point of.

---

