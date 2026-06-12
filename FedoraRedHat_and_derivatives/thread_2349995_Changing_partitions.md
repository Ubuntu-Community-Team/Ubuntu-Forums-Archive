---
title: "Changing partitions"
date: 2017-01-20
forum: Fedora/RedHat and derivatives
---

### Post by Infamshxr on 2017-01-20
Hello all, I can't get a good response from other forums I'm on, so I gotta ask here since you guys are so helpful, even though I'm not currently running a 'buntu variant. I was on Debian Jessie and was having problems so I switched to Fedora 25 (since all Debian-based distros had the same issue). 

When testing different distros I had partitioned my drive to test other distros, and I failed to notice that Fedora partitioned my drive with a seperate boot partition. 

So my drive ended up looking like this...
Sda1 - Debian - 63gb ext4
Sda2 - boot - 1gb ext4
Sda3 - Fedora - 54gb LVM 

I did some research and decided to create a new boot partition, then copy the files from my current boot partition to it. I still have to update the UUID in my fstab to reflect the changes though. 

So my drive looks like this...
Sda1 - boot - 1gb ext4(new partition, boot flag set)
Sda2 - free space - 63gb
Sda3 - boot - 1gb ext4(current boot partition)
Sda4 - Fedora - 54gb LVM

I want to delete my current boot partition, so I can combine sda2, sda3, and sda4 into one partition, but I'm not sure if there's anything else I need to do besides changing the fstab file with the UUID of the new boot partition. 

Right now the computer boots fine, but I'm not sure which partition it's booting from. I'm assuming the original boot partition though.

---

### Post by howefield on 2017-01-20
Moved to the "*Fedora/RedHat and derivatives*" forum.

---

### Post by oldfred on 2017-01-20
Redhat/Fedora default install is normally the full drive LVM configuration with a separate /boot partition.
Some that dual boot, suggest just using a standard ext4 partition like Ubuntu.

       May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Then you can confirm UUIDs in Boot partition and grub menu match.

---

### Post by Infamshxr on 2017-01-21
> **oldfred said:**
> Redhat/Fedora default install is normally the full drive LVM configuration with a separate /boot partition.
Some that dual boot, suggest just using a standard ext4 partition like Ubuntu.

       May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Then you can confirm UUIDs in Boot partition and grub menu match.

I'm not able to boot a Ubuntu flavor live CD. My hardware just won't let it boot. Fedora is basically the only one that boots and unfortunately boot-repair is not available in the repos. Which is why I'm going about this manually.

Right now it basically comes down to whether or not I need to do anything besides changing the UUID of the boot partition in fstab then update my grub config file. If that's all I need to do, then great, I'm about done. But I'm not sure if there's anything else that needs to be changed

---

### Post by Infamshxr on 2017-01-21
Subscribing.

---

### Post by oldfred on 2017-01-21
I think Boot-Repair will work in Fedora also.
It is not in the Ubuntu repo, but installed separately.

---

