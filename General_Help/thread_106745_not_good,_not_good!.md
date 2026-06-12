---
title: "not good, not good!"
date: 2005-12-21
forum: General Help
---

### Post by luminoso on 2005-12-21
I.. i have been using ubuntu dor 3 mouths more and less..
I realy love it! But.. yesterday i need to install windows, onde my second hard disk to copy files from my mobile phone.

Everything worked fine.. so.. i need to put the files on my etx3 partition.
I used Ext2 Installable filesystem 1.10a.

It only detected my /boot partition.. since i have space there, i put my photos in /boot/ with windows.

but...

When starting up i get o couple of errors abou superblock error and a lot of confusing partitions when type "fidsk -l"

I installed Gparted and deleted some of them.

Once i restarted... puff! No ubuntu.. only /boot partition.

Now..
I can i recover my partitions back withou reinstall everything?

Thanks for all,
luminoso

---

### Post by localzuk on 2005-12-21
It sounds like you have deleted the ubuntu partitions. Take a look at [http://www.lissot.net/partition/partition-09.html](http://www.lissot.net/partition/partition-09.html) it might provide some insight into how to get back the partition table.

Also, just as a piece of advice for future reference, it is a bad idea to use the /boot partition for anything other than the kernel image and bootloader.

---

### Post by luminoso on 2005-12-21
Thanks.. !! i will try right now! :)

---

