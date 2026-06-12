---
title: "defragmenting disks"
date: 2006-04-04
forum: Desktop Environments
---

### Post by krypto_wizard on 2006-04-04
I recently deleted lot of stuff from my ubuntu box.

Is there anything like disk defragmenter in Linux(Ubuntu) to reallocate the files.

Thanks

---

### Post by nanotube on 2006-04-04
the ext3 filesystem that is used by ubuntu does not require defragmenting, because unlike windows filesystems it is efficient enough to keep itself in order. :)

---

### Post by drummer on 2006-04-04
No, you don't need to defragment the drive if you're using the ext3 file system (which is the default for Ubuntu). ext3 (and other linux file systems) handle fragmentation much better than windows file systems and even after months of use have minimal fragmentation. I've recently reinstalled my comp to use dapper (I did a clean install on a separate disk) but when I was using Hoary and even after upgrading to Breezy I had about 5% fragmentation after 7-8 months. And that was with an often fairly full disk. Do that in windows, with fat32 especially, and I'd have closer to 100% fragmentation easily.

---

### Post by krypto_wizard on 2006-04-04
good to know that linux is doing so good.

---

### Post by PhoenixP3K on 2006-04-07
Well that's a great thing to know, but I'm still curious. Is there a defragmentation tool for servers or something. We also have to consider that Dapper will be dist-upgrade and some will not make a clean install. After "a few years" you're bound to require some defragmenting no?

---

### Post by Enfenion on 2006-04-14
How do you know how much your disk is fragmented?

---

### Post by PhoenixP3K on 2006-04-15
Well since it's pretty much an irrelevent problem under linux you will have to look for a program that can check your disc. But as mentionned earlier you won't need defragmenting. Try googling to find a program that does that.

---

### Post by jongkind on 2006-04-15
[QUOTE=Enfenion]How do you know how much your disk is fragmented?[/QUOTE]

After 30 boots Ubuntu executes disk scanning. When you take a carefull look you see the level of fragmentation as soon is this scanning is finished. In my case: the partion containing Ubuntu is 2% defragmented, the partition that contains the home folders is 9% defragmented. I would say that the latter level of fragmentation is quiet significant. 

Herman

---

