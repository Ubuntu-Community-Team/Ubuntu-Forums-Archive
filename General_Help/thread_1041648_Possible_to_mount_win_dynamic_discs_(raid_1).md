---
title: "Possible to mount win dynamic discs (raid 1)?"
date: 2009-01-16
forum: General Help
---

### Post by él Mero on 2009-01-16
I have four harddrives:
#1 Ubuntu 8.10 x64 installed
#2 Windows XP Pro x86 installed
#3 Dynamic disc, raided in win (raid 1) with #4
#4 Dynamic disc, raided in win (raid 1) with #3

I want to access the raid in Ubuntu. Do I need to re-raid #3 and #4 in some way under Ubuntu, to have raid 1 there also, or can I simply mount the already created windows raid 1 in Ubuntu?

---

### Post by fjgaude on 2009-01-17
I can't say if a program called **dmraid** will work or not with Windows software raid. It's in the repository:

```
sudo apt-get install dmraid
```

Read the **man** page for it and see if you can figure out how to mount your raid. If not let us know.

---

### Post by Ben Webber on 2009-01-18
I was actually trying to figure out the same thing _[over here]("http://ubuntuforums.org/showthread.php?t=1041899")_. After a hell of a lot of scouring, I found two documents in the kernel documentation I think should help you:
[LIST]
[*]_[The Linux NTFS filesystem driver]("http://www.mjmwired.net/kernel/Documentation/filesystems/ntfs.txt")_, and
[*]_[Logical Disk Manager (Dynamic Disks)]("http://www.mjmwired.net/kernel/Documentation/ldm.txt")_.
[/LIST]

I suggest following the **mdadm** approach, as it seems to be simpler. What you will end up with is something like this:

[LIST]
[*]sda1 (Windows)
[*]sda*x* (Ubuntu), *x* belongs to {2,3,4,...,n}
[*]md0 (RAID array)
[/LIST]

This is the most comprehensive documentation I could find on the procedure, though. Let us know how it works out. As well, I'll post how my own setup works out in this thread if you don't beat me to it.

---

