---
title: "Boot up error msg. after upgrade to LTS version"
date: 2012-05-03
forum: Desktop Environments
---

### Post by tdlam on 2012-05-03
I upgraded my Xubuntu install form 11.10 to the latest LTS release. All is working ok except I get this error on boot up:
```
The disk drive for UUID=37f713a-f180-4641-af50-3ed1db9c5a9 is not ready or not present. Continue to wait, or Press S to skip mounting or M for Manual recovery
```

the machine boots ok after that but it is slowing things down. I was wondering if anyone has any ideas how to make this error go away.

Thanks in advance for your time.

---

### Post by mips on 2012-05-03
Please post the contents of your **/etc/fstab** file here.
When you boot up write down the **UUID** of the problematic drive/partition before pressing 'S' for skip and post it here so we know which drive/partition it is.
While you are at it also post the output of **sudo fdisk -l** & **sudo blkid** here.

---

### Post by tdlam on 2012-05-03
Ok thanks for the quick replay. Under etc/ there is a folder called fstab.d and it is empty. I enabled "show hidden files" but the still is nothing there.


fdsisk -1 output:
```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x41ab2316


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   187164671    93581312   83  Linux
/dev/sda2       187164672   195371007     4103168   82  Linux swap / Solaris
```



blkd output:
```
/dev/sda1: UUID="10f58ff0-25dd-40aa-a293-e9037e069284" TYPE="ext4" 
/dev/sda2: UUID="d6dfe302-e80c-4f61-86c6-0e92280992e0" TYPE="swap" 
```



UUID error is:

UUID=37f7134a-f180-4641-af50-3ed1dbd9c5a9

---

### Post by mips on 2012-05-03
> **tdlam said:**
> Ok thanks for the quick replay. Under etc/ there is a folder called fstab.d and it is empty. I enabled "show hidden files" but the still is nothing there.

:confused:

Check again (it's not inside fstab.d but in the root of /etc) or try this command from a terminal **cat /etc/fstab**

---

### Post by tdlam on 2012-05-03
that did it here it is:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=10f58ff0-25dd-40aa-a293-e9037e069284 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=37f7134a-f180-4641-af50-3ed1dbd9c5a9 none            swap    sw              0       0

```

---

### Post by mips on 2012-05-03
You have mismatched UUIDs for the swap partition.

Will get back to you shortly with a possible fix.

In the mean time post the output of **free -m** as i wanna see if your swap partition is mounted.

---

### Post by tdlam on 2012-05-03
you are a nice person BTW. I just wanted to tell you that I appreciate all you help. Thank you again for what you are doing.

---

### Post by tdlam on 2012-05-03
free -m:

```
             total       used       free     shared    buffers     cached
Mem:          2013        898       1114          0         97        370
-/+ buffers/cache:        430       1582
Swap:            0          0          0

```

---

### Post by mips on 2012-05-03
Try this,

```
gksu leafpad /etc/fstab
```

Edit the file so the UUID matches the one in [COLOR="red"]red[/COLOR] below, save & close,
> # /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=10f58ff0-25dd-40aa-a293-e9037e069284 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=[COLOR="Red"]d6dfe302-e80c-4f61-86c6-0e92280992e0[/COLOR] none            swap    sw              0       0



Next we need to see if it matches the initramfs resume file else hibernating wont work, so post the output of **cat /etc/initramfs-tools/conf.d/resume** here




.

---

### Post by mips on 2012-05-03
> **tdlam said:**
> free -m:

```
             total       used       free     shared    buffers     cached
Mem:          2013        898       1114          0         97        370
-/+ buffers/cache:        430       1582
Swap:            0          0          0

```

From this you can see that your swap partition is not mounted as it's 0 bytes in size.

---

### Post by mips on 2012-05-03
> **tdlam said:**
> you are a nice person BTW. I just wanted to tell you that I appreciate all you help. Thank you again for what you are doing.

Thanks. Don't thank me just yet as we have not solved the problem yet :biggrin:

---

### Post by tdlam on 2012-05-03
I changed it like you said


heres the output you requested:


RESUME=UUID=37f7134a-f180-4641-af50-3ed1dbd9c5a9

---

### Post by mips on 2012-05-03
> **tdlam said:**
> I changed it like you said


heres the output you requested:


RESUME=UUID=37f7134a-f180-4641-af50-3ed1dbd9c5a9

Ok, that's also wrong, let's fix it.

```
gksu leafpad /etc/initramfs-tools/conf.d/resume
```

Edit the file so the UUID matches the one in [COLOR="red"]red[/COLOR] below, save & close,
> RESUME=UUID=[COLOR="Red"]d6dfe302-e80c-4f61-86c6-0e92280992e0[/COLOR]

Next we need to update initramfs,
```
sudo update-initramfs -u
```

You're done, reboot your PC and see if you still get the skip error and then paste the output of **free -m** here again so I can see if it's working.

I'll wait for you to reboot and get back to me.

---

### Post by tdlam on 2012-05-03
YOU did it! Thank you so very much for your help

free-m:

```
 total       used       free     shared    buffers     cached
Mem:          2013        822       1190          0         91        336
-/+ buffers/cache:        394       1618
Swap:         4006          0       4006

```

You and this community ARE great.

---

### Post by mips on 2012-05-03
> **tdlam said:**
> YOU did it! Thank you so very much for your help

free-m:

```
 total       used       free     shared    buffers     cached
Mem:          2013        822       1190          0         91        336
-/+ buffers/cache:        394       1618
Swap:         4006          0       [COLOR="Red"]4006[/COLOR]

```

You and this community ARE great.

Yip it's working as you can now see the swap is mounted.

Glad I could help ;)



TAGS: The disk drive for UUID= is not ready or not present. Continue to wait, or Press S to skip mounting or M for Manual recovery UUID Mismatch Swap /etc/fstab /etc/initramfs-tools/conf.d/resume

---

### Post by tdlam on 2012-05-03
God bless you and everyone that is important to you in your life.

Thank you again and thanks for being such a fine example of the helpful linux community.

Take care.

I am marking this post as solved thanks to your good kindness.

---

### Post by mips on 2012-05-03
Thank you for the kind words tdlam.

---

