---
title: "hard drive re-devicing problem"
date: 2009-02-22
forum: General Help
---

### Post by mrose1120 on 2009-02-22
hi,
I have a ubuntu server 64bit installation (8.10) and it seems randomly when i reboot, it will renumber the devices.  
Like yesterday it was working fine, and the 40gb hard drive I had (which is IDE) was sda, then today I boot up and the 40gb is sdb and the 500gb is sdb..
any ideas? I run some vmware test machines on the 500gb hard drive, so when it starts up backwards, they don't work

---

### Post by prinny42 on 2009-02-22
What kind of drives are we talking about here?  Further, what is each drive used for?

For instance, is it a 500GB internal drive with nothing but the aforemention vmware test machines on it with a 40GB external drive installed with Ubuntu, or what?

---

### Post by mrose1120 on 2009-02-22
> **prinny42 said:**
> What kind of drives are we talking about here?  Further, what is each drive used for?

For instance, is it a 500GB internal drive with nothing but the aforemention vmware test machines on it with a 40GB external drive installed with Ubuntu, or what?

the 500gb drive only has vmware isos and vmdk files on it.
the 40gb is what ubuntu was installed on, and the 40gb is a ide
the 500gb is a sata drive and is just mounted via fstab

---

### Post by Seq on 2009-02-22
> **mrose1120 said:**
> hi,
I have a ubuntu server 64bit installation (8.10) and it seems randomly when i reboot, it will renumber the devices.  
Like yesterday it was working fine, and the 40gb hard drive I had (which is IDE) was sda, then today I boot up and the 40gb is sdb and the 500gb is sdb..
any ideas? I run some vmware test machines on the 500gb hard drive, so when it starts up backwards, they don't work

If you reference your partitions via UUID in fstab, then the disk ordering does not matter. You can find the UUID using the blkid command (where sda3 is the partition as it currently appears in your system)

```
 blkid /dev/sda3
```

Here is an example of my fstab:

```
# /dev/sda3
UUID=27d4bb27-9bd2-41e8-bc0a-737c84120533 /               ext3    noatime,errors=remount-ro 0       1
# /dev/sda4
UUID=9895ce8e-80da-49d0-b7c0-3be64b710e4d /home           ext3    noatime        0       2
# /dev/sda5
UUID=1c57ede9-7988-4deb-b312-b699aa15f2fe none            swap    sw              0       0
```

Ubuntu uses UUID by default (including the server edition). I'm guessing that your root filesystem on your 40GB disk is mounted by UUID, and it is only your 500GB disk that is not.

---

