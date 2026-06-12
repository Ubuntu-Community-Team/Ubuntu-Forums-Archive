---
title: "Mysterious 18.04 boot failure"
date: 2018-08-31
forum: Desktop Environments
---

### Post by vergil.si on 2018-08-31
Hi. If could get any assistance, I'd appreciate it. I don't have a huge amount of experience with the groundwork of the linux boot process. After researching the issue, my encrypted drive seems like it also further complicates things. Also, I have secure-boot enabled, if that makes things even worse.
Dell XPS 15 9570
18.04

Installed fresh about a week ago, all was well, other than some weird driver issues that would occur when I closed the laptop and reopened it, sometimes forcing me to power cycle it. Today, I went to turn it on, and instead of being prompted to enter my drive encryption password, I get the kubuntu image just sitting there. I hit F2 to check out what was going on and got the following...

[IMG]https://ibb.co/cKJwV9[/IMG]
[https://ibb.co/cKJwV9](https://ibb.co/cKJwV9)

It drops me into a busybox shell after failing a number of times.

I looked around at a couple similar issues, and tried to use an ubuntu live USB to check if I could at least see the drive, but ```
fdisk -l
``` only displays the two partitions /dev/sda1 and /dev/sda2 of the Live USB.

Any help would be appreciated.

---

### Post by vergil.si on 2018-08-31
So, just in case anyone else experiences this, I actually found the solution with the help of a co-worker. Somehow, my BIOS (by itself) switched from AHCI, to RAID. When I switched it back to AHCI, all was well again.

---

### Post by oldos2er on 2018-08-31
Thank you for posting the solution! Would you please mark the thread 'Solved' using Thread Tools at the top of the page, so that others may benefit from the answer?

---

