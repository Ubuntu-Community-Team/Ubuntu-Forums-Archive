---
title: "/home not mounted -&gt; can't use system"
date: 2009-04-28
forum: General Help
---

### Post by Niniel on 2009-04-28
Hello,

I updated from 8.10 to 9.04 and it seemed to have gone without a problem. Except when the system rebooted after the upgrade, it couldn't mount my /home partition, which is on an SD card which in turn is in a Transcend USB-adapter. It used to work in 8.10, however, so I started with the old kernel the next time and it started just fine.
Sometime later I forgot to boot with the old kernel, but it loaded ok anyway, so I figured all was well and deleted the old kernel with new the Cleanup utility.
However, today it won't boot anymore, and I'm getting the same error as right after the upgrade.
I suppose my best bet is to put the old kernel back on, but how do I do that?
Or are there alternatives? Is there a way to make the new kernel work for me?

Thanks.

---

### Post by Woody1987 on 2009-04-28
It looks like the UUID for your home partition is incorrect in fstab. Open a terminal and type sudo blkid. This will give the UUID of all your partitions. find the one that corresponds to your home partition and copy it into your /etc/fstab file.

---

### Post by Niniel on 2009-04-29
That command only finds sda partitions 1 - 4, the flash card is sdb. Fdisk also doesn't see it.
Seems to me that the new kernel no longer supports the USB adapter and that I need the old kernel back. But how?

I am getting one other error while booting although I'm not sure if it has anything to do with this problem:
> modprobe: FATAL: Could not load /lib/modules/2.6.28.11-generic/modules.dep: no such file or directory

---

### Post by dcstar on 2009-04-29
> **Niniel said:**
> That command only finds sda partitions 1 - 4, the flash card is sdb. Fdisk also doesn't see it.
Seems to me that the new kernel no longer supports the USB adapter and that I need the old kernel back. But how?

I am getting on other error while booting although I'm not sure if it has anything to do with this problem:

a) Reinstall the appropriate modules packages;

b) Don't stuff around with the cleanup program - it isn't worth the trouble.

---

### Post by Woody1987 on 2009-04-29
instead of using UUID, try using the path to the device, i.e. /dev/sdb1

---

### Post by Niniel on 2009-04-29
That didn't work, but as it turns out, this was a case of hardware failure - namely, of the USB port I used to plug my adapter into. On a lark, I tried a different one, and now the computer boots fine again. Stupid USB ports, soon they will all be useless... :(

---

