---
title: "System Ubuntu 11.10 cvf now running for 10 hrs."
date: 2011-11-26
forum: Desktop Environments
---

### Post by kurtkurtosis on 2011-11-26
I am new to Linux and am trying to backup Ubuntu 11.10 to a 1TB drive (mostly for practice). I am aware of several methods: dd, cvpzf, rsync, Rsnapshot, rdiff+, Clonezilla. I am just getting my feet wet with cvpzf.

I am using the following command which seems to work as about 8 GB of the 64 GB SSD have been backed up to a 1 TB WD green drive.

I used the following command:

tar cvpzf ubuntu.tgz –exclude=/proc –exclude=/lost+found –exclude=/ubuntu.tgz –exclude=/mnt –exclude=/sys —exclude=/media /

The system I am using is a XEON 3.3 GHz with 16GB of memory using a SuperMicro X9 1155 Mobo. So its a pretty powerful system. Why is it taking 1o hrs thus far to backup 9 GB? The SSD is 64 GB while the the operating system & data only consume about 4GB. Is cvpzf copying all the sectors? That's what Windows Home Server 2011 does, but that only take about 30 minutes at best for the same system

THX

---

### Post by kurtkurtosis on 2011-11-27
I think I understand the problem now.

[http://www.novell.com/support/search.do?cmd=displayKC&docType=kc&externalId=7004153&sliceId=1&docTypeID=DT_TID_1_1](http://www.novell.com/support/search.do?cmd=displayKC&docType=kc&externalId=7004153&sliceId=1&docTypeID=DT_TID_1_1)

It has to do with a virtual file /proc/kcore which consumes no disk space but somehow the backup process tries to copy the file. The file size is ~140TB. So the solution is probably to exclude the file as part of the backup script.

---

