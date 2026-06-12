---
title: "Swap UUID does not show up in blkid etc.!!??"
date: 2009-01-15
forum: General Help
---

### Post by Piraja on 2009-01-15
Hey, I know I caused my swap UUID to change since I messed about with an external disk installation (I'm not going into details now, but trying to install Debian Etch on an external USB HDD turned out to be trickier than I thought; the thing is that the Debian "expert mode" installer insists on using the internal HDD's swap space and does not even offer an alternative or ask me about this detail...).

And I know from experience (I've encountered this before) that I must edit fstab. However, this blkid output puzzles me:

```
/dev/sda1: UUID="0B92DAEF522D1731" TYPE="ntfs" 
/dev/sda2: LABEL="HP_TOOLS" UUID="A438-DD58" TYPE="vfat" 
/dev/sda3: UUID="E056567B56565280" LABEL="HP_RECOVERY" TYPE="ntfs" 
/dev/sda5: UUID="a1e4fde2-dfe2-4d47-9951-f4062b5d6f38" TYPE="ext3" 
/dev/sda6: TYPE="swap" 
/dev/sda7: UUID="74fb6d68-7846-4ecb-97b6-38b65ab5947c" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sdb1: UUID="c08e23c1-aa25-4cad-9692-77f4c553bd0e" TYPE="ext3" 
/dev/sdb3: UUID="2bc32022-27a8-47d5-8d33-83c86e23618c" TYPE="ext3" 
/dev/sdb5: TYPE="swap"
``` 

Firstly, I don't have an external USB drive plugged in at the moment (showing as sdb). Secondly, why does it say just "swap" without UUID?

Well, the next thing to do might be simply typing man blkid...

... and figuring out I should maybe try this: sudo blkid -c /dev/null

```
/dev/sda1: UUID="0B92DAEF522D1731" TYPE="ntfs" 
/dev/sda2: LABEL="HP_TOOLS" UUID="A438-DD58" TYPE="vfat" 
/dev/sda3: UUID="E056567B56565280" LABEL="HP_RECOVERY" TYPE="ntfs" 
/dev/sda5: UUID="a1e4fde2-dfe2-4d47-9951-f4062b5d6f38" TYPE="ext3" 
/dev/sda6: TYPE="swap" 
/dev/sda7: UUID="74fb6d68-7846-4ecb-97b6-38b65ab5947c" TYPE="ext3"
``` 

Still no UUID for swap. I don't get it.

---

### Post by Piraja on 2009-01-15
See also this:

```
piraja@berserkerberos:~$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2009-01-15 21:40 0B92DAEF522D1731 -> ../../sda1
lrwxrwxrwx 1 root root 10 2009-01-15 23:37 74fb6d68-7846-4ecb-97b6-38b65ab5947c -> ../../sda7
lrwxrwxrwx 1 root root 10 2009-01-15 23:37 a1e4fde2-dfe2-4d47-9951-f4062b5d6f38 -> ../../sda5
lrwxrwxrwx 1 root root 10 2009-01-15 21:40 A438-DD58 -> ../../sda2
lrwxrwxrwx 1 root root 10 2009-01-15 21:40 E056567B56565280 -> ../../sda3
```

The swap partition (sda6) is not listed, as you see.

I did "swapon" and I have to do it at each boot, after which the usual "0 %" indeed shows up in Conky.

---

### Post by Piraja on 2009-01-15
... and this:

```
piraja@berserkerberos:~$ sudo vol_id /dev/sda6
[sudo] password for piraja: 
ID_FS_USAGE=other
ID_FS_TYPE=swap
ID_FS_VERSION=2
ID_FS_UUID=
ID_FS_UUID_ENC=
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=
piraja@berserkerberos:~$ 
```

---

### Post by Piraja on 2009-01-15
Well, here comes a workaround. I found it here at UF, having already figured out that I could possibly just remove the wrong UUID from fstab, searching by the terms "swap remove wrong uuid fstab". I replaced the wrong UUID with the device path, as follows:

```
/dev/sda6 none            swap    sw              0       0
```

I don't really like this solution, or rather workaround, because I believe it is generally a good idea to have devices pointed at in fstab by UUIDs instead of other possible alternatives (i.e. dev path, label).

---

### Post by Yashiro on 2009-01-15
Try swapoff, reformatting the partition and setting swapon using gparted and not any other tools.

Or generate a new UUID for the swap, maybe. 
[http://pwet.fr/man/linux/commandes/uuidgen](http://pwet.fr/man/linux/commandes/uuidgen)

---

### Post by caljohnsmith on 2009-01-15
Oops, didn't see Yashiro's post where he says the same thing I was going to say.

---

### Post by Piraja on 2009-01-15
Thank you Yashiro and caljohnsmith! 

I used the Gparted method, did sudo vol_id /dev/sda6, received the new UUID and edited fstab accordingly.

Such posts make the present absence of the "Thank you" button ever more conspicuous.

(Hmmm... Also "Mark this thread as 'Solved'" has disappeared...?)

---

### Post by Yashiro on 2009-01-15
Send the cheque in the post. Or a Pot Noodle. ;)

---

### Post by Piraja on 2009-01-16
You *do* have a money-back guarantee policy, don't you?

Seriously speaking, swap still isn't automatically activated at boot, in spite of the fact that the swap UUID shown by blkid is identical with the one in fstab. Well, the difference is indeed that now blkid shows the swap UUID, whereas it previously did not. Yet, it has this funny detail that while all other lines have UUID first, sda6 has "TYPE=swap" before the UUID...

```
piraja@berserkerberos:~$ sudo blkid -c /dev/null
/dev/sda1: UUID="0B92DAEF522D1731" TYPE="ntfs" 
/dev/sda2: LABEL="HP_TOOLS" UUID="A438-DD58" TYPE="vfat" 
/dev/sda3: UUID="E056567B56565280" LABEL="HP_RECOVERY" TYPE="ntfs" 
/dev/sda5: UUID="a1e4fde2-dfe2-4d47-9951-f4062b5d6f38" TYPE="ext3" 
[COLOR="Red"]/dev/sda6: TYPE="swap" UUID="c1c7221c-8ea1-4ea6-b47f-ffb829194ae0" [/COLOR]
/dev/sda7: UUID="74fb6d68-7846-4ecb-97b6-38b65ab5947c" TYPE="ext3" 
piraja@berserkerberos:~$
```

Strange!!??

---

### Post by caljohnsmith on 2009-01-16
That does seem strange that blkid would list the type before the UUID; I've never seen that before, so I don't know if that is OK or a sign that something is wrong. Considering that you are still having problems using your swap though, I'm inclined to think it's a sign something is not quite right. Also, have you lost your Ubuntu splash screen on start up? That's also usually a symptom of having problems with the swap partition. How about doing:
```
cat /etc/initramfs-tools/conf.d/resume
```
If that file shows a UUID which should be for your swap partition, then how about trying:
```
sudo swapoff -a
sudo mkswap -U $(awk -F"=" '{print $3}' /etc/initramfs-tools/conf.d/resume) /dev/sda6
```
Also, modify your fstab to use the UUID for the swap partition shown in the resume file above, then reboot and post the output of:
```
sudo fdisk -lu
sudo blkid -c /dev/null
cat /etc/fstab
cat /etc/initramfs-tools/conf.d/resume
free
```
And we can work from there if you want.

---

### Post by Piraja on 2009-01-16
I edited fstab, removing the UUID of sda6 and putting /dev/sda6 instead. However, this did not help: when I rebooted I noticed an error message telling me the mount-point for swap doesn't exist (can you tell me why this error is not shown in either dmesg or /var/log/messages?).

So I have to keep on typing "sudo swapon /dev/sda6" every time I boot, as it seems. Actually the quiet boot has been interrupted lately also by something else &#8212; this has been happening ever since my unsuccessful attempt to install Debian Etch on an external HDD a couple of days ago &#8212; so maybe I'd better take a closer look at the log files, anyway.

**EDIT**: Thanks caljohnsmith, you were quick this time; I posted before I read your reply. I will try your suggestions &#8212; back in a jiffy...

---

### Post by Piraja on 2009-01-16
Caljohnsmith, I followed your suggestions &#8212; thank you so much for helping me out on a Friday night (heh, at least here in Helsinki it's Friday night).

After I took the first steps you suggested, I rebooted and the quiet splash was no longer interrupted, which is of course a good sign. Here is the output for the four commands:

```
sudo fdisk -lu
[sudo] password for piraja: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x80d2f3ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   168730694    84365316    7  HPFS/NTFS
/dev/sda2       291604480   293701631     1048576    c  W95 FAT32 (LBA)
/dev/sda3       293703344   312581807     9439232    7  HPFS/NTFS
/dev/sda4       168730695   291595814    61432560    5  Extended
/dev/sda5       168730758   198033254    14651248+  83  Linux
/dev/sda6       289652013   291595814      971901   82  Linux swap / Solaris
/dev/sda7       198033318   289651949    45809316   83  Linux

```

```
piraja@berserkerberos:~$ sudo blkid -c /dev/null
[sudo] password for piraja: 
/dev/sda1: UUID="0B92DAEF522D1731" TYPE="ntfs" 
/dev/sda2: LABEL="HP_TOOLS" UUID="A438-DD58" TYPE="vfat" 
/dev/sda3: UUID="E056567B56565280" LABEL="HP_RECOVERY" TYPE="ntfs" 
/dev/sda5: UUID="a1e4fde2-dfe2-4d47-9951-f4062b5d6f38" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="d02199ed-022b-41fe-ba59-c7b640f1839a" 
/dev/sda7: UUID="74fb6d68-7846-4ecb-97b6-38b65ab5947c" TYPE="ext3"
```
 
```
piraja@berserkerberos:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=a1e4fde2-dfe2-4d47-9951-f4062b5d6f38 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=74fb6d68-7846-4ecb-97b6-38b65ab5947c /home           ext3    relatime        0       2
# /dev/sda6
UUID=d02199ed-022b-41fe-ba59-c7b640f1839a swap sw 0 0
# /dev/scd0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

```
piraja@berserkerberos:~$ cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=d02199ed-022b-41fe-ba59-c7b640f1839a
```

```
pirajae@berserkerberos:~$ free
             total       used       free     shared    buffers     cached
Mem:       1796352     621996    1174356          0      16192     245528
-/+ buffers/cache:     360276    1436076
Swap:            0          0          0

```

Conky still shows "no_swap%", by the way (**edit**: well, I suppose that's how it should be, too, since I turned swap off before rebooting...?).

**Re-edit**: No, after "swapon /dev/sda6" and another reboot, still "no_swap%" in Conky, until I do "swapon" again.

---

### Post by plucky on 2009-01-16
> # /dev/sda6
UUID=d02199ed-022b-41fe-ba59-c7b640f1839a swap sw 0 0




That line should read ```
# /dev/sda6
UUID=d02199ed-022b-41fe-ba59-c7b640f1839a [color=red]none[/color] swap sw 0 0
```

Hope that helps.

Good Luck

---

### Post by Piraja on 2009-01-16
> **plucky said:**
> That line should read ```
# /dev/sda6
UUID=d02199ed-022b-41fe-ba59-c7b640f1839a [color=red]none[/color] swap sw 0 0
```
Hey Plucky, that's a great observation! I bet I'm having no longer "no swap%" after reboot (just a moment...) &#8212; **BINGO!** Thanks for having such a keen eye!

Have a *GREAT* weekend all of you!

---

### Post by stormtrooprdave on 2009-02-17
> **Yashiro said:**
> Try swapoff, reformatting the partition and setting swapon using gparted and not any other tools.

Thanks, I had conky showing noswap% after a partition resize, this worked and took about 30 seconds to do

---

