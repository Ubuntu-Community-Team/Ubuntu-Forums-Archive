---
title: "NTFS problem, maybe"
date: 2009-01-03
forum: General Help
---

### Post by mrkane27 on 2009-01-03
Hi!

I run a computer dual-booting Kubuntu 8.04 and Windows XP SP2, and I'm getting the following behavior:

When I try to defragment one of my NTFS partitions, with less than 20% free space, the defragmenter software only shows me about a tenth of the space as used, and stops defragmenting after under 5 seconds, telling me that it couldn't defragment some files. I'm okay with that, but I should have 80% of that window filled with colored bars, which I don't.

Why I'm posting this here is, I'm wondering whether the NTFS driver that comes with my Linux might do something non-standard, not update indices, that kind of thing, and writing that drive from Linux is the only potentially non-standard thing I've done.

Has anybody experienced anything similar?

Thank you,
Vlad

---

### Post by Hybrid-photog on 2009-01-03
I'm not fully up to speed with the current state of NTFS support in Linux. All I can remember is that NTFS support is pretty much limited to read-only access.

Unless someone else knows otherwise, I'd not attempt to do anything regarding defragmenting NTFS partitions from within Linux.

---

### Post by albinootje on 2009-01-03
> **Hybrid-photog said:**
> I'm not fully up to speed with the current state of NTFS support in Linux. All I can remember is that NTFS support is pretty much limited to read-only access.

Unless someone else knows otherwise, I'd not attempt to do anything regarding defragmenting NTFS partitions from within Linux.

Years ago the NTFS driver that came with the Linux kernel was read-only, because read/write access was experimental.
However, there were other projects working on it.
Since a while you can use ntfs-3g (Comes with Hardy and Intrepid, not sure about Gutsy) for read/write on NTFS-partitions.

---

### Post by mrkane27 on 2009-01-03
> **Hybrid-photog said:**
> Unless someone else knows otherwise, I'd not attempt to do anything regarding defragmenting NTFS partitions from within Linux.

I meant Disk Defragmenter, under Windows XP.

Other than that, I don't have any problems with that partition. When running Windows I can read all the files written under Linux without a glitch. It's just that I'm not sure as to what's causing the defragmentation problem, and I don't want something suddenly crashing on me.

---

