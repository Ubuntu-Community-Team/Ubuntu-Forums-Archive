---
title: "SATA RAID 0 dmraid"
date: 2006-06-13
forum: Desktop Environments
---

### Post by jewishj on 2006-06-13
I am having some problems installing Dapper to an SATA RAID 0.  I have installed dmraid and it finds the raid correctly (I have to use the motherboard sw raid or else it won't boot from it), however, when I try to format the drive.. it fails.

The issue I believe (from what I've been able to find from this post: [http://ubuntuforums.org/showthread.php?t=67498&page=2](http://ubuntuforums.org/showthread.php?t=67498&page=2)) is that dmraid thinks that the raid has a stripe size of 16K when it actually has a stripe size of 64k.  The author of the post suggests that he had the same issue and that updating the stripe size manually to 64K using dmsetup fixed it.  I cannot figure out how to do this (I'm pretty new to linux) after searching through the forums/wiki/google/man pages - maybe I'm just blind.  In any case, if anyone has any experience with this and could give me the command to use to do this.

Thanks

---

### Post by Anything Generic on 2006-06-13
I just ran into this problem myself.  Check out these 2 links, and format via terminal window.  Gparted woudln't format the drives for me either, but the quoted command below worked.

[http://www.ubuntu-in.org/wiki/SATA_RAID_Howto]("http://www.ubuntu-in.org/wiki/SATA_RAID_Howto")

[https://wiki.ubuntu.com/FakeRaidHowto]("https://wiki.ubuntu.com/FakeRaidHowto")

> sudo mkfs.ext3 /dev/mapper/nvidia_gahhaaab1

---

### Post by jewishj on 2006-06-13
Sorry.. fixed - please ignore

---

