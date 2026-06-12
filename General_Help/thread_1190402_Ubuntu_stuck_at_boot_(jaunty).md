---
title: "Ubuntu stuck at boot (jaunty)"
date: 2009-06-17
forum: General Help
---

### Post by ubv1308 on 2009-06-17
Bios -> grub -> splash then get stuck


Couple of minutes after that, this start to appear :

Reading files needed to boot

[ 929.515727 ] res 41/40:00:5f:b0:3d/00:01:00:00/40 Emask 0x409 (media error) <F>
[ 929.515727 ] ata1.00: status: { DRDY ERR }
[ 929.515727 ] ata1.00: error: { UNC }
[ 929.515727 ] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 929.515727 ] ata1.00: irq_stat 0x4000008
[ 929.515727 ] ata1.00: cmd 60/08:00:5f:b0:3d/00:01:00:00/40 tag 0 ncq 4096 in 

The [xxx.xxxx] keep changing start from around 386 finishing around close to 1000. I'm guessing it's in relation to the fact that the drive is 1000 Gigs.

After that nothing, it's a blank screen.

So by going to [http://ata.wiki.kernel.org/index.php/Libata_error_messages](http://ata.wiki.kernel.org/index.php/Libata_error_messages), I know the error are telling me it can't read the HD. UNC :Uncorrectable error - often due to bad sectors on the disk 

So something got corrupt (Ubuntu freezed and I rebooted manually).

What do I do from there ? Reading other thread maybe doing a fsck could help but I'm not sure how to run it.

Thanks


Edit : My setup is something like that, but that's from memory :
Disk 1 - 1TB
/		ext3	~35 GB	/dev/sda1	Primary partition
SWAP	  linux-swap	6 GB	/dev/sda5	Logical partition
/home		ext3	~30 GB	/dev/sda6	Logical partition
Data		JFS	Rest	/dev/sda7	Logical partition

Disk 2 - 1 TB
DATA	JFS	300G	/dev/sdb1	Primary partition
DATA	JFS	Rest	/dev/sdb5	Logical partition

Edit 2 : Booted the live cd and tried : sudo shutdown -rF now
Computer restarted but saw nothing happen and got stuck at the same place as usual.

Edit 3 : For fsck : live cd -> terminal, did fsck on everything except swap (I think, is it suppose to check that quickly, like only a couple of seconds), still same thing at boot. Here's what I just did :

ubuntu@ubuntu:~$ sudo fsck.jfs /dev/sdb1
fsck.jfs version 1.1.12, 24-Aug-2007
processing started: 6/18/2009 2.7.57
Using default parameter: -p
The current device is:  /dev/sdb1
Block size in bytes:  4096
Filesystem size in blocks:  80616170
**Phase 0 - Replay Journal Log
Filesystem is clean.
ubuntu@ubuntu:~$ sudo fsck.jfs /dev/sdb5
fsck.jfs version 1.1.12, 24-Aug-2007
processing started: 6/18/2009 2.8.18
Using default parameter: -p
The current device is:  /dev/sdb5
Block size in bytes:  4096
Filesystem size in blocks:  163573822
**Phase 0 - Replay Journal Log
Filesystem is clean.
ubuntu@ubuntu:~$ sudo fsck.jfs /dev/sda7
fsck.jfs version 1.1.12, 24-Aug-2007
processing started: 6/18/2009 2.9.31
Using default parameter: -p
The current device is:  /dev/sda7
Block size in bytes:  4096
Filesystem size in blocks:  220628669
**Phase 0 - Replay Journal Log
Filesystem is clean.
ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
/dev/sda1: clean, 143288/3066000 files, 1225793/12257587 blocks
ubuntu@ubuntu:~$ sudo fsck /dev/sda6
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
/dev/sda6: clean, 12824/2444624 files, 1013040/9765504 blocks

---

### Post by artshark on 2009-06-18
Having same issue, help would be appreciated for both of us!

---

