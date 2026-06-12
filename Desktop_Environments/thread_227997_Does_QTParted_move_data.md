---
title: "Does QTParted move data?"
date: 2006-08-02
forum: Desktop Environments
---

### Post by yumigator on 2006-08-02
PartitionMagic stopped functioning on my computer, so I'm trying to use QTParted off a Knoppix LiveCD to make my Windows partition smaller and the Linux partitions larger.

Looking at the usage charts on Disk Defragmenter, which comes with Windows, It seems like there's a chunk of data that is sitting by itself close to the end of the partition. Will QTParted move this for me to safely resize, or will it just write over it? And if not, what utilities can I use to move that data to the beginning of the partition?

Thanks

---

### Post by The Seeker on 2006-08-02
As long as you've defragged you should be fine; QTParted won't overwrite the chunk you're talking about.

Disclaimer: That being said, just remember there's always a slight risk in partitioning a HDD so make sure you've backed up any important files.

---

