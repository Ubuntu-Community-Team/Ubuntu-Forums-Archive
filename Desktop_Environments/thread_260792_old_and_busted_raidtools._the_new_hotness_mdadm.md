---
title: "old and busted: raidtools. the new hotness: mdadm"
date: 2006-09-19
forum: Desktop Environments
---

### Post by Locke2053 on 2006-09-19
My internet searches have taught me that any forward-thinking progressive, like myself, should build a RAID using mdadm, and not with raidtools.

In fact, Ubuntu seems to already use mdadm for *something.* Without having explicitly set up anything, I have /dev/md0-24 alread existing on my filesystem.

Why is that?

If I use mdadm to create a new RAID, do I have to start at md25? Would making my new one md0 overwrite anything?

One more question on RAID: The only good documentation I found on mdadm is here: [http://www.linuxdevcenter.com/lpt/a/2776](http://www.linuxdevcenter.com/lpt/a/2776)

But that guide presumes you have partitions on your disks. It doesn't explain what kind of partitions or why they are needed. Can someone explain why I would need to create a RAID from partitioned disks, instead of partitioning a RAID itself?

Thanks.

---

### Post by mike3k on 2006-09-19
The presence of the device nodes doesn't mean those md devices actually exist. To see which RAID devices already exist, type:
```
cat /proc/mdstat
```If there are no RAID devices, it will say file not found.

Here's another article about setting up RAID: [http://www.macmegasite.com/node/1731]("http://www.macmegasite.com/node/1731")

---

### Post by Locke2053 on 2006-09-19
me@host:~$ cat /proc/mdstat
Personalities :
unused devices: <none>


So what does that indicate?

---

