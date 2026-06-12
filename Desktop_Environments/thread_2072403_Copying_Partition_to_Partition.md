---
title: "Copying Partition to Partition"
date: 2012-10-17
forum: Desktop Environments
---

### Post by fjgaude on 2012-10-17
I used **dd** at terminal to copy a bootable partition to another bootable partition, like so:

```
sudo dd if=/dev/sdc1 of=/dev/sda2
```

All went well, as expected. On a third drive that the BIOS points to I booted to an OS and ran grub-update. Booted to thinking it was the sda2 partition from the grub menu. But no now both sda2 and sdc1 have exactly the same OS and data. I then changed the UUID of sda2 to another random number using Gparted. Still no go after running grub-update again.

Does anyone know what I should do to get grub, grub menu to see the real sda2?

Thank you!

---

### Post by oldfred on 2012-10-17
dd is an exact copy. 

But UUIDs of all partitions are in grub and fstab. So updating grub from inside your install should work, but you have to update fstab as both partitions will have the same entries.

---

### Post by fjgaude on 2012-10-17
I was thinking of having to do as you suggest. But it seems that an update-grub should take care of it all, but no. I suppose the data that grub scans is in the header of each partition.

I'll change the fstab with the new UUID for the sda2 partition and see if that does the trick. I think it might take more than that, but we will see tomorrow... have to run now.

Thanks for coming back. Stay tuned!

---

### Post by fjgaude on 2012-10-18
Well, I've put the new UUID in fstab for sda2 and re-run update-grub, but still... from a third partition grub menu has the same data for both sda2 and sdc1 and loads occordingly. I can mount sda2 and do see it is there but grub2.0 simply looks at things that were placed there when dd-ing sdc1 to sda2, to decide there's only one partition, not two.

There is something else that needs to be changed so that grub knows these two as different drives.

Help, please!

---

### Post by fjgaude on 2012-10-18
```
frank@cutie:~$ sudo update-grub
[sudo] password for frank: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-17-generic
Found initrd image: /boot/initrd.img-3.5.0-17-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 12.04.1 LTS (12.04) on /dev/sda2
Found Ubuntu 12.04.1 LTS (12.04) on /dev/sdc1
Found Ubuntu 11.10 (11.10) on /dev/sdc2
done

frank@cutie:~$ sudo blkid
[sudo] password for frank: 
/dev/sda1: LABEL="database" UUID="76e508bc-2395-456b-8527-14ca510d7341" TYPE="ext4" 
/dev/sda2: LABEL="12.04.1" UUID="f998c6a7-6cb8-4c15-8ebe-ba407b9cb950" TYPE="ext4" 
/dev/sdb1: UUID="cb0b5c7c-cd5b-4528-8cc5-ed4469bf682f" TYPE="ext4" 
/dev/sdc1: LABEL="12.04 LTS" UUID="5cfab316-422c-4796-abd9-764a0235c780" TYPE="ext4" 
/dev/sdc2: LABEL="11.10" UUID="2b8a2d69-60ad-41fc-8088-d54c410caf29" TYPE="ext4" 
/dev/sdc3: LABEL="BAKUP" UUID="8a047fa8-3597-452e-a7cf-569207ca65d5" TYPE="ext4" 
/dev/sdc5: UUID="abd9b257-a183-46a4-98d7-1a39684e16b6" TYPE="swap"
 
frank@cutie:~$ df
Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/sdb1       62766044 30154584  29423084  51% /
udev             3929728       12   3929716   1% /dev
tmpfs            1575572      948   1574624   1% /run
none                5120        8      5112   1% /run/lock
none             3938928      548   3938380   1% /run/shm
none              102400       64    102336   1% /run/user
/dev/sda1       91073640 60132284  26315080  70% /home/database
/dev/sdc3      110680912 86239412  18819228  83% /media/BAKUP

```

What is wrong? This data taken when booting from sdb1. Remember I copied sdc1 to sda2 and then changed the UUID on sda2. GRUB2 doesn't find a difference between the partitions and only loading the sdc1 even when it says it's on sda2.

Please help?

---

### Post by grahammechanical on 2012-10-18
I do not know if this will help. I think that what you are doing is out of my league but who knows.

update-grub simply runs this script /usr/sbin/update-grub

> #!/bin/sh
set -e
exec grub-mkconfig -o /boot/grub/grub.cfg "$@"

It re-writes grub.cfg but it does not install it into the MBR. So, the already existing grub.cfg will be in control.

You may get better results if you run this command

```
sudo grub-install /dev/sda
```

(change sda to the drive/partition you want) after running update-grub. That will install grub into the MBR of that drive.

I had similar issues recently. I have 1 x 12.04 and 3 x 12.10 on one hard disk and things were fine until the 3 x 12.10 had grub 1.99 replaced by grub 2.0. Running update-grub from the OS I wanted in control did not change the grub menu. I had to run grub-install /dev/sda from that OS in order to put it in charge of booting.

Regards.

---

### Post by fjgaude on 2012-10-18
Okay, and thanks... I did what you said, install on drive but I think I did that before I changed the UUID. Will do it again!

---

### Post by fjgaude on 2012-10-18
I see the issue but don't know the correct way to fix it:

```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Ubuntu 12.04.1 LTS (12.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-f998c6a7-6cb8-4c15-8ebe-ba407b9cb950' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos2'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  **f998c6a7-6cb8-4c15-8ebe-ba407b9cb950**
	else
	  search --no-floppy --fs-uuid --set=root f998c6a7-6cb8-4c15-8ebe-ba407b9cb950
	fi
	linux /boot/vmlinuz-3.2.0-32-generic root=UUID=**5cfab316-422c-4796-abd9-764a0235c780** ro quiet splash $vt_handoff
	initrd /boot/initrd.img-3.2.0-32-generic
```

The old UUID, i.e., the one from the source copy is used instead of the new UUID.

OKAY! I manually changed the UUID in grub.conf and it booted into the copied to partition. Now I know if I run update-grub again it'll be wrong as before. Will study what it takes to fix the issue.

---

### Post by mikeym on 2012-10-18
Sorry, not sure what step you've missed (or has otherwise gone wrong) but you appear to be trying to do this:

[https://help.ubuntu.com/community/MovingLinuxPartition](https://help.ubuntu.com/community/MovingLinuxPartition)

Perhaps it might shed some light.

---

### Post by fjgaude on 2012-10-18
Thanks for the link. The only thing I may have not done is modify the grub.conf file in the destination file. That file is grub1.99 while the main boot file is grub2.0. The link wishes to boot into the new destination OS. I don't wish that except through the grub menu produced by OS in sdb1.

We will see... I boot from drive sda the OS on sdb1. The copied OS is in partition sda2.

I'll there one way or the other. Thanks again for all the replies.

**NOTE: by changing the destination grub.conf file to indicate the new UUID all is well now.**

---

