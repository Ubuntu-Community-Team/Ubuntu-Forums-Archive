---
title: "Hard disk does not pass fsck, and I can't boot!"
date: 2009-03-26
forum: General Help
---

### Post by Fixman on 2009-03-26
Today, when I booted my Ubuntu I took a surprise: it started booting, and after some time the common (and hateful) orange text telling me a HD check is going on appeared. However, it didn't go to 1% before the screen turned black and a terminal appeared, telling me to fsck manually. When I do that, it tells me that an Inode has bad data, and I tell it to erase it. However, then it tells me the next inode also has bad data, and the other, etc.

I can't seem any way to boot, I'm stuck in a terminal without network services and writing this from my XP partition. Can I have some help?

---

### Post by Fixman on 2009-03-26
bump!

---

### Post by Rallg on 2009-03-26
When you were dropped to Terminal, it should have told you that the offending partition was unmounted, yes? Don't use fsck on a mounted partition.

Often, when fsck complains, you will see numerous complaints. In the past, I have simply accepted the default for each complaint, then proceeded to boot (exit). Once, it complained upon re-boot, so again I accepted its complaints. Eventually, problem solved.

Maybe that won't work for everybody, but if it doesn't work, maybe your system really does have some fundamental file system error.

For future use: On my computer, I have two installations of the same Ubuntu, with a common Home directory and a spare FAT32 partition. I only update one installation at a time, delaying several days before I boot to the other and update it. That way, if some update is misapplied, I can boot to the opposite system. Or, if fsck objects to a file system, I can boot to the other.

If you do something like that, the extra installation doesn't have to have all the programs, just enough to get by.

---

