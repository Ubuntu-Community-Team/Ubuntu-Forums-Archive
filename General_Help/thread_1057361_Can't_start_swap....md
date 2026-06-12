---
title: "Can't start swap..."
date: 2009-02-01
forum: General Help
---

### Post by Montblanc_Kupo on 2009-02-01
So... this is odd. I recently added more ram to My system so I wanted to resize the swap file to accommodate (hopefully) using the hibernate / suspend modes.

Here's the weirdness...

The resize went fine... system boots, I used a LiveCD and told it to use swapon in gparted from the LiveCD. No complaints. So I tried hibernate. Said it couldn't locate the swap and to try swapon -a.

In terminal I type sudo swapon -a and get this:

[quote="My Stupid Computer"]swapon: cannot stat /dev/disk/by-uuid/9b5ec41b-c11e-4dfb-bcd8-3e4ed2c4f0f5: No such file or directory[/quote]

Uhm... gparted inside ubuntu and from the livecd both see the swap partition. If I use gparted, it doesn't complain at all about Me right clicking and chosing "swapon"... puts the little mounted keychain icon next to it and doesn't argue at all. System monitor says it sees the correct amount of swap in the resources tab and it's even using a tiny bit of it. But if I try to hibernate or use swapon again.. I get the same error.

uhm... wth?

---

### Post by taurus on 2009-02-01
What are the outputs of these commands from a terminal?

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
free -m
```

---

### Post by Boomhauer on 2009-02-01
maybe when you resized your swap partition it changed the uuid. run ```
blkid
``` and then compare your swap partition uuid to your /etc/fstab swap partition uuid.  if they are different, change the one in fstab to match the one in blkid

---

### Post by Montblanc_Kupo on 2009-02-01
fdisk -l
```
Disk /dev/sda: 185.2 GB, 185283624960 bytes
255 heads, 63 sectors/track, 22526 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       22526    78541785    5  Extended
/dev/sda5           12749       12800      417658+  83  Linux
/dev/sda6           12801       16960    33415168+  83  Linux
/dev/sda7           22201       22526     2618563+  82  Linux swap / Solaris
```

blkid
```
/dev/sda1: UUID="C27C13EF7C13DD4B" TYPE="ntfs" 
/dev/sda5: UUID="259b747c-63f2-40c0-9c0c-58fb8a10d8ad" TYPE="ext3" SEC_TYPE="ext2" LABEL="boot" 
/dev/sda6: UUID="e46277f5-a7af-4c77-9027-b29352956ab7" TYPE="ext3" LABEL="Ubuntu" 
/dev/sda3: TYPE="swap" UUID="7cfd4364-7a3a-4410-94d1-d03a92b32584" 
/dev/sda4: LABEL="Storage" UUID="06864f23-0990-4959-b4e1-6851af94868b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="a8ca9ceb-bea5-4820-8057-04dcda886c1d"
```

cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=e46277f5-a7af-4c77-9027-b29352956ab7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=259b747c-63f2-40c0-9c0c-58fb8a10d8ad /boot           ext3    relatime        0       2
# /dev/sda2
UUID=9b5ec41b-c11e-4dfb-bcd8-3e4ed2c4f0f5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

free -m
```
             total       used       free     shared    buffers     cached
Mem:          1009        986         22          0          7         99
-/+ buffers/cache:        879        129
Swap:         2557         18       2538

```

I'm not super-savvy yet about what that all means... but I did see that there are some inconsistancies... like it's still listing partitions I deleted such as "Storage". And it's listing two swap partitions?

Here's a screenshot from gparted to get a more visual idea of what the drive actually looks like right now.

[IMG]http://www.shinyimage.com/misc/gparted_screenshot.jpg[/IMG]

---

### Post by taurus on 2009-02-01
From a terminal, edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and replace the old UUID for swap with this new one.

```
UUID=**a8ca9ceb-bea5-4820-8057-04dcda886c1d**   none   swap   sw   0   0
```
Save it and reboot.

Now see if swap partition is working.

```
free -m
```
By the way, what are you planning to do that 40GB unallocated space?  Do you want to give that space to root filesystem (/dev/sda6)?  You have to do that with gparted from either Ubuntu LiveCD or GParted LiveCD, [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php).

Unless I am missing something, I don't see two swap partitions from your screenshot!

---

### Post by caljohnsmith on 2009-02-01
I just wanted to add that if you use the strategy Taurus gives for getting your swap partition working again, it's quite likely you will also have to update your /etc/initramfs-tools/conf.d/resume file and also your /boot/initrd images since they are hard-coded with your swap UUID. You can check it with:
```
gksudo gedit /etc/initramfs-tools/conf.d/resume
```
And that file should contain your new swap UUID "a8ca9ceb-bea5-4820-8057-04dcda886c1d", so if it still has the old UUID "9b5ec41b-c11e-4dfb-bcd8-3e4ed2c4f0f5", then it would be good to correct it. If you have to change it, then after you save that file do:
```
sudo update-initramfs -u -k all
```
And that will update all your /boot/initrd images with the new UUID. Good luck and let us know how it goes.

---

### Post by Montblanc_Kupo on 2009-02-01
I was referring to these two lines from the blkid output:

[b]/dev/sda3: TYPE="swap" UUID="7cfd4364-7a3a-4410-94d1-d03a92b32584" 
/dev/sda7: TYPE="swap" UUID="a8ca9ceb-bea5-4820-8057-04dcda886c1d"[/b]

Not sure why it was listing both of those as swap, and only one of them is actually listed in gparted.

> By the way, what are you planning to do that 40GB unallocated space?

That is where fedora is going to go a little later tonight. :) Well.. part of it anyway.

Anyway... the advice you guys gave seems to have fixed it. I haven't tried hibernate yet, but there are no more errors from swapon and it's auto mounting the swap at startup in gparted now, so I'm assuming it's fixed.

Thanks a lot! ... now if I can just get My video working agian. :( heh

---

### Post by caljohnsmith on 2009-02-01
> **Montblanc_Kupo said:**
> I was referring to these two lines from the blkid output:

[b]/dev/sda3: TYPE="swap" UUID="7cfd4364-7a3a-4410-94d1-d03a92b32584" 
/dev/sda7: TYPE="swap" UUID="a8ca9ceb-bea5-4820-8057-04dcda886c1d"[/b]

Not sure why it was listing both of those as swap, and only one of them is actually listed in gparted.

Did you delete the sda3 swap partition when you were doing your partition changes? If so, that would explain why "sudo blkid" still sees that partition; "sudo blkid" prints your partitions and UUIDs from its last cached file, and that could be out-of-date as you experienced. In my experience, I've found it is usually better to run blkid as:```

sudo blkid -c /dev/null
```
And that way it forces blkid to re-analyze your current partitions and print the results. Anyway, glad your swap partition is working OK so far. Cheers and enjoy your Ubuntu install. :)

---

### Post by Montblanc_Kupo on 2009-02-01
> **caljohnsmith said:**
> In my experience, I've found it is usually better to run blkid as:```

sudo blkid -c /dev/null
```

Groovy noodles. Yeah... that returns the right info... another mystery solved scooby. :) hehe thanks.

Now... how much do you know about nvidia graphic drivers LOL.

---

### Post by Montblanc_Kupo on 2009-02-02
I have another question if anyone knows...

I was looking to use hibernate on a desktop... and eventually it will do it.. (although very slowly) and it always gives Me an error about "trying to free already free IRQ 17" something along those lines... and sits for a while... eventually it will go to sleep. Is there some way to figure out what's wrong.. make things go faster?

Also... how do I wake it back up? No key wakes it up... and hitting power reboots.

---

