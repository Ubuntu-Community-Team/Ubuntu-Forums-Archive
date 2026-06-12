---
title: "splash cut short"
date: 2009-01-20
forum: General Help
---

### Post by ZOOstation on 2009-01-20
I'm having splash troubles at startup. It starts fine, but right before the status bar would start filling up, it disappears and I get a plain text boot, beginning with "Reading files needed to boot..."

I've tried [the fix listed here]("https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/205990/comments/39") but all my UUIDs matched up.

However, using the Partition Editor tool there is no swap partition listed. I recently erased an old partition and expanded the main one to fill the empty space, so it's possible I unwittingly deleted the swap partition. How could I go about fixing that incongruence?

Also, I get a text screen I never used to get. First there's the one that says Loading GRUB, but it used to go straight from there to the splash. Now there's one in between that notifies me which kernel is booting, even though I set it to load one by default and a waiting time of 0.

---

### Post by caljohnsmith on 2009-01-20
How about posting the output of the following commands:
```
sudo fdisk -lu
sudo blkid -c /dev/null
cat /etc/fstab
cat /etc/initramfs-tools/conf.d/resume
```

---

### Post by ZOOstation on 2009-01-21
```
joey@Lappy:~$ sudo fdisk -lu

[INDENT]Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc466c466

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *          63   195366464    97683201    5  Extended
/dev/sda5             126   195366464    97683169+  83  Linux[/INDENT]

joey@Lappy:~$ sudo blkid -c /dev/null

[INDENT]/dev/sda5: UUID="1db8f79b-2fcd-4c06-9b41-38746af941e6" TYPE="ext3"[/INDENT]

joey@Lappy:~$ cat /etc/fstab

[INDENT]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=1db8f79b-2fcd-4c06-9b41-38746af941e6 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=40c9074a-7b83-49e9-ae6d-380d05d8b4aa none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0[/INDENT]

joey@Lappy:~$ cat /etc/initramfs-tools/conf.d/resume

[INDENT]RESUME=UUID=40c9074a-7b83-49e9-ae6d-380d05d8b4aa[/INDENT]
```

---

### Post by mcduck on 2009-01-21
Yes, you have clearly deleted the swap partition (since "fdisk -l" doesn't show any).

I recommend resizing some partition again and creating at least small swap partition in the freed space.

When that's done, run "blkid" to get correct UUID's for your partitons, and edit both /etc/fstab and /etc/initramfs-tools/conf.d/resume so that they have correct UUIDs. (the resume file should have UUID of the swap partition. If it doesn't, usplash will fail during boot)

---

### Post by caljohnsmith on 2009-01-21
> **mcduck said:**
> Yes, you have clearly deleted the swap partition (since "fdisk -l" doesn't show any).

I recommend resizing some partition again and creating at least small swap partition in the freed space.

When that's done, run "blkid" to get correct UUID's for your partitons, and edit both /etc/fstab and /etc/initramfs-tools/conf.d/resume so that they have correct UUIDs. (the resume file should have UUID of the swap partition. If it doesn't, usplash will fail during boot)
If you change the fstab and resume file with the new swap partition UUID, it turns out you also have to regenerate all the initrd images to use the new swap UUID, because the swap partition UUID is hard-coded into the initrd images. So you would also have to do:
```
sudo update-initramfs -u -k all
```
That could certainly work, and I used to do it that way too until I found out you can simply change the new swap partition's UUID to the original swap UUID with one single command.

**ZOOstation**, if you decide to recreate a swap partition as mcduck describes, how about when you are done change the swap partition UUID to the original swap UUID:
```
sudo swapoff -a && sudo mkswap -U 40c9074a-7b83-49e9-ae6d-380d05d8b4aa /dev/[COLOR="Blue"]sdaX[/COLOR]
```
And replace sdaX with the new swap partition (for instance it might be sda6). Then reboot, and you should be all set if all goes well. If for some reason you really don't want a swap partition and would rather have a swap file, let me know and I can help with that if you want. Otherwise let us know how it goes. :)

---

### Post by ZOOstation on 2009-01-21
What's a reasonable size for my new swap partition?

---

### Post by ZOOstation on 2009-01-25
Back in business! Thanks guys.

One thing of interest: somewhere between both of your instructions I seem to have created two swap partitions at the same UUID. GParted shows sda6 but doesn't show sda7, but blkid gives me:
```
/dev/sda1: UUID="cbb8c644-ddc5-4bee-8990-921d43093fb7" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="1db8f79b-2fcd-4c06-9b41-38746af941e6" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="40c9074a-7b83-49e9-ae6d-380d05d8b4aa" 
/dev/sda7: UUID="40c9074a-7b83-49e9-ae6d-380d05d8b4aa" TYPE="swap"
```
Also, GParted has no sda1, only sda2 on which sda5 and 6 are mounted.

---

### Post by caljohnsmith on 2009-01-25
How about posting:
```
sudo fdisk -lu
sudo blkid -c /dev/null
cat /etc/fstab
cat /etc/initramfs-tools/conf.d/resume

```

---

### Post by ZOOstation on 2009-01-31
```
me@Lappy:~$ sudo fdisk -lu

[INDENT]Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc466c466

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *          63   195366464    97683201    5  Extended
/dev/sda5             126   189229634    94614754+  83  Linux
/dev/sda6       189229698   195366464     3068383+  82  Linux swap / Solaris[/INDENT]

me@Lappy:~$ sudo blkid -c /dev/null

[INDENT]/dev/sda5: UUID="1db8f79b-2fcd-4c06-9b41-38746af941e6" TYPE="ext3" 
/dev/sda6: UUID="40c9074a-7b83-49e9-ae6d-380d05d8b4aa" TYPE="swap"[/INDENT]

me@Lappy:~$ cat /etc/fstab

[INDENT]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=1db8f79b-2fcd-4c06-9b41-38746af941e6 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=40c9074a-7b83-49e9-ae6d-380d05d8b4aa none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0[/INDENT]

me@Lappy:~$ cat /etc/initramfs-tools/conf.d/resume

[INDENT]RESUME=UUID=40c9074a-7b83-49e9-ae6d-380d05d8b4aa[/INDENT]
```

---

### Post by caljohnsmith on 2009-01-31
I think the discrepancy is that you should always run "sudo blkid -c /dev/null" after any partition changes, because if you just use "blkid" or even "sudo blkid", it just prints the cached blkid file which is not accurate. Everything looks fine from what you posted, so I don't think you have anything to be concerned about as far as your swap partition is concerned. :)

---

### Post by ZOOstation on 2009-01-31
Thanks. You'll both have my official "thanks" as well, whenever the feature is re-enabled.

---

