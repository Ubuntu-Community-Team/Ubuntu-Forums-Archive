---
title: "Problem with ext2 partition"
date: 2005-12-06
forum: Desktop Environments
---

### Post by Neutrino on 2005-12-06
Hello,
I am having a problem with my ext2 partition. I am using QTparted to resize this partition. When i try to resize it told me that the partition is corrupted and i need to use fsck to check it.
I looked around and i found a way to run fsck at startup and to force it to check  the parttiion.
But fsck didn't find any error!
What should i do to force it check deeply the ext2 partition? 
Do you know any other tools to check ext2 partition that is more powerful than fsck??

regards,

---

### Post by Neutrino on 2005-12-06
Any idea?? :(

---

### Post by fourchannel on 2005-12-06
it might be bad blocks on your HD.

EDIT: make sure whatever partition you affect is unmounted, just in case you didn't know.

get your favorite live cd and fire it up. breezy live would be fine ;)

open up a terminal, light up a cigarette, and type in this command:

```
sudo e2fsck -t ext2 -fcc /dev/**device**
``` 
and replace device with your harddrive and partition number. so if the partition you wanted to check was the second one on your primary harddrive it would be  /dev/**hda2**

depending on the size of your drive it could take from 30 minutes to 2 days.

the -f option tells e2fsck to force a check. and the -cc tells it to check each block by doing a read/write test (non-destructively), and after all is done it updates the badblock table on the partition.

in my opinion i think it would be a good idea to convert your partition over to ext3, which is a journaled version of ext2. basically a safety measure in which if something happens to the drive, you can replay the journal to find out what it was last working on.

*in that case* you would instead run these commands:

```
sudo tune2fs -j /dev/device
sudo e2fsck -t ext3 -fcc /dev/device
``` 
and then have a stab at QTparted.

if that doesn't fix it, then consider the most entertaining way to destroy your harddrive. like 10 story fall shock proof test.

but really if that doesn't fix it then i dont know what could cause it.

---

### Post by Neutrino on 2005-12-07
Thank you for your help fourchannel!
The partition i want to check is the root partition.
How can i unmount it. I launched the recovery mode and when i do 'umount /dev/hda6'
and 'fsck -fcc /dev/hda6'
It tells me that the partition is mounted read only and i think it doesn't check itdepply.
I don't have a liveCd. (it takes time to download)
How can i unmount the root partition et remount it after verifying partition to reboot???

Thanks,

---

### Post by Original Brownster on 2005-12-07
[QUOTE=Neutrino]Think you for your help fourchannel!
The partition i want to check is the root partition.
How can i unmount it. I launched the recovery mode and when i do 'umount /dev/hda6'
and 'fsck -fcc /dev/hda6'
It tells me that the partition is mounted read only and i think it doesn't check itdepply.
I don't have a liveCd. (it takes time to download)
How can i unmount the root partition et remount it after verifying partition to reboot???

Thanks,[/QUOTE]
mmmm tricky I think. If you unmount / you cant do anything as it's where all the programs are!

You really need a liveCd as it will be easy that way. 

If your adventurous you could look into using 'chroot' and 'env-update'; If you have another partition spare and large enough, you could copy your / /etc /var /tmp /bin /usr directories to there, mount it as say /mnt/tmproot then you would use 'chroot' which updates the system to use the newly copied files as '/'. 
With this done you could unmount your original root partition and check it.

Sorry I don't know much more than that; you could check out the installation of 'Gentoo' which uses chroot as part of the install process.

HTH,

Regards

---

### Post by fourchannel on 2005-12-07
this *might* work. boot into recovery mode.

```
mount -t ext2 -o remount -o ro /dev/device /
``` and then try the fsck check.

if you wanted to convert it to ext3, run the tune2fs command, then the mount command, then the e2fsck for ext3 one.

what it does is keep data from being written to the harddrive. i can't remember if fsck is or isn't allowed to bypass that. it couldn't hurt to try though.

once it's done

```
mount -t ext2 -o remount -o rw /dev/device
``` and then reboot

---

