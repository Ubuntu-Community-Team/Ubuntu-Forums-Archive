---
title: "Change root partition from primaty to logical"
date: 2009-05-23
forum: General Help
---

### Post by vlsi on 2009-05-23
I have the following structure on my HDD:
1)Logical Disk  - Primary - Not formatted - Laptop's Recovery
2)Logical Disk  - Primary - NTFS - Vista
3)Logical Disk  - Unallocated - Free Space - 
4)Logical Disk  - Primary - Ext3 - Ubuntu
5)Extended 
    - Logical Disk  - LinuxSwap2

I am trying to test Win7 RC but I can't install it on (2). It states that disk has already maximum number of primary partitions. Is it possible to change my root partition from primary to a logical one. 
I know it's a long shot, but I can't reformat my root because I can't afford the time to set my Ubuntu again.

PS. Using Partition Manager (Windows) I have an option to Make Partition Logical for my ext3/root. Is that safe? I would prefer gparted as I trust it more...

---

### Post by unutbu on 2009-05-23
Please post the output of ```

sudo fdisk -l
```

---

### Post by vlsi on 2009-05-23
Sure,

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x54a86bd2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1545    12402688   27  Unknown
/dev/sda2   *        1546       17326   126756162    7  HPFS/NTFS
/dev/sda3           20496       24106    29005357+  83  Linux
/dev/sda4           24107       24321     1726987+   5  Extended
/dev/sda5           24107       24321     1726956   82  Linux swap / Solaris

I think that between sda2 and sda3 is the unallocated space I 'm referring to. It's about 26.5GBs. 
Should I format it in some fs to help you?

---

### Post by unutbu on 2009-05-23
First run this command
```

sudo sfdisk -d /dev/sda > PT.txt
```

It will create a text file called PT.txt in your home directory.
Take a look inside and you will see it is a report of your partition table.
Please post this file.

I will manually edit this file to change sda3 to sda6. 
I'll post a new PT.txt file, and show you a command which will rewrite your 
partition table using the new PT.txt.

This will make your Linux partition a logical partition.
The location of the partition and the data within it is not touched. Only the
name changes. That's all it takes to make it a logical partition however.
You can then use GParted to create a new sda3 primary partition for Win7.

---

### Post by vlsi on 2009-05-23
Ok, here it is

---

### Post by unutbu on 2009-05-23
Below are instructions on how to change sda3 to sda6.
Before you begin, please post your /boot/grub/menu.lst. 
Depending on how it is written, we may need to update it.
Once we make sure that it is okay, then proceed with the instructions below.

----------------------------------------------------------------------

Boot from a LiveCD. 

Download the attached new_PT.txt file.
Then run
```

sudo umount /dev/sda{1,2,3,4,5,6}
```

Don't worry if the umount command returns an error message saying those partitions are not mounted. 
I'm just trying to make sure no partition on sda is mounted. 

This will rewrite the partition table:
```

sudo sfdisk --no-reread -f /dev/sda -O PT.txt < new_PT.txt
```

The PT.txt that you posted is a good safe-guard against trouble. 
If anything goes wrong, we can use that file to restore your current partition table. 

Since we've changed the device number of your Linux partition, we'll also need to
update the GRUB bootloader so it can find and boot the Linux partition.
```

sudo grub
grub> root (hd0,5)
grub> setup (hd0)
grub> quit

```
Now reboot and see if you can boot and that your linux partition is now called sda6.

---

### Post by vlsi on 2009-05-23
Here is the menu.lst as you requested:

(You can remove the .txt, I just put it to upload it.)

---

### Post by unutbu on 2009-05-23
I made some changes to the menu.lst in anticipation of the partition table change.

While booted into Ubuntu, save the attached new menu.lst.txt to /boot/grub/menu.lst.
There is an extra boot stanza added at the end so you can continue to boot off of sda3.
The normal default stanza has been changed to boot off of sda6.

Once sda3 has been successfully renamed sda6, then you can delete the extra boot stanza
at the end of /boot/grub/menu.lst:
```

title		Ubuntu 8.04.2 on sda3
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=d5ad4030-15fe-457e-8531-ab4151b92d7f ro quiet splash
initrd		/boot/initrd.img-2.6.24-24-generic
quiet
```

After you have saved this new menu.lst to /boot/grub/menu.lst, perhaps you should reboot and make sure you can boot the last option "Ubuntu 8.04.2, (sda3)" just to make sure everything is hunky-dory up to this point.

Once that is done, boot off the LiveCD and proceed with the instructions in post #6.

---

### Post by vlsi on 2009-05-23
A warning is displayed after I run
```
sudo sfdisk --no-reread -f /dev/sda -O PT.txt < new_PT.txt
```

Disk /dev/sda: 24321 cylinders, 255 heads, 63 sectors/track
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0+   1544-   1545-  12402688   27  Unknown
/dev/sda2   *   1545   17325-  15781- 126756162    7  HPFS/NTFS
/dev/sda3      20495   24105    3611   29005357+  83  Linux
/dev/sda4      24106   24320     215    1726987+   5  Extended
/dev/sda5      24106+  24320     215-   1726956   82  Linux swap / Solaris
Warning: bad partition start (earliest 387262891)
cannot build surrounding extended partition

---

### Post by unutbu on 2009-05-23
Indeed. Sorry about that. I forgot to expand the extended partition. I've updated the new_PT.txt attachment in post #6.
Re-download it and try again.

---

### Post by vlsi on 2009-05-23
Similar error (different ) once more. The output is displayed on the attachment

---

### Post by unutbu on 2009-05-23
I apologize. I forgot that the first logical partition needs a 63 sector gap between itself and the start of the extended partition. Post #6 has been updated. Hopefully I've got it right this time.

---

### Post by vlsi on 2009-05-23
Again sorry to bother you but I have a grub error this time

grub>
      setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,5)/boot/grub/stag
e2 /boot/grub/menu.lst"... failed

Error 22: No such partition

---

### Post by unutbu on 2009-05-23
Okay, I think the OS doesn't know about the changes we've made to the partition table.
Try running 
```

sudo partprobe

```
followed by the grub commands. If "sudo partprobe" throws an error message, try rebooting the LiveCD and then issuing the grub commands.

---

### Post by vlsi on 2009-05-23
OK, I did as advised from your last post. I successfully managed to see the correct grub menu and boot to my Ubuntu.
Then I proceded to installing Win7 on the unallocated partition.
Now, I can't see grub, so I tried to reinstall it. I booted from the live CD and I got the following:

   grub> find /boot/grub/stage1

   Error 15: File not found

   grub> find grub/stage1

   Error 15: File not found

Fdisk displays:

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x54a86bd2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1545    12402688   27  Unknown
/dev/sda2   *        1546       17326   126756162    7  HPFS/NTFS
/dev/sda3           17326       20495    25458688    7  HPFS/NTFS
/dev/sda4           20495       24321    30732376+   5  Extended
/dev/sda5           24107       24321     1726956   82  Linux swap / Solaris


and here is a screenshot where the ext3 partition looks like unallocated space, any help would be much appreciated...:confused:

---

### Post by unutbu on 2009-05-23
Okay, I think we can fix this with testdisk.

Boot the LiveCD.
Install the testdisk package.
Run
```

sudo testdisk
```

Select "No Log", "Proceed", "Intel", "Analyse", "Quick Search"
When asked "Should  TestDisk search for partition created under Vista", answer Y.
Select "Deeper Search". 

testdisk should find the missing Linux partition, sda6.

Use the up/down arrows to select the Linux partition. Press 'p' to make sure you can see the files inside this partition.

Use the right/left arrows to change the partition state from D (for deleted) to L (for Logical).

Press "Enter" to continue.
Select the option to write the new partition.

Your partition table should then be fixed.

---

### Post by vlsi on 2009-05-23
> **unutbu said:**
> Use the right/left arrows to change the partition state from D (for deleted) to L (for Logical).
Press "Enter" to continue.


The only options I am presented here are D (delete with structure: OK), P (primary with structure: OK), * (primary bootable with structure: bad)...

---

### Post by unutbu on 2009-05-23
When you press 'p', are you able to see the files in the missing Linux partition?
I'm not sure why testdisk is not allowing you to restore the Linux partition. 
However, perhaps we fix this by hand. If you'd like to try that,
post PT.txt:
```

sudo sfdisk -d /dev/sda > PT.txt

```

---

### Post by vlsi on 2009-05-24
> **unutbu said:**
> When you press 'p', are you able to see the files in the missing Linux partition?
I'm not sure why testdisk is not allowing you to restore the Linux partition. 
However, perhaps we fix this by hand. If you'd like to try that,
post PT.txt:
```

sudo sfdisk -d /dev/sda > PT.txt

```

Yes, I am able to see the contents of my ext3 partition, when I press 'p'.
Running the sfdisk I get the following message:"Warning: extended partition does not start at a cylinder boundary.DOS and Linux will interpret the contents differently."
And here is the output PF.txt.

---

### Post by unutbu on 2009-05-24
Attached is WinLin_PT.txt. It includes an entry for sda6.

As before, to write the partition table to disk, run
```

sudo sfdisk --no-reread -f /dev/sda -O PT.txt < WinLin_PT.txt
```

Regarding the error message "extended partition does not start at a cylinder boundary.DOS and Linux will interpret the contents differently.": I don't think this will affect you unless you want to access your Linux partition from within Windows. If you do, then to fix this you could run GParted and shrink the swap space a little bit, move the Linux partition to the right, then shrink the extended partition. GParted rounds partitions to cylinder boundaries by default. 

We can talk about that more if you want to do that, but either way, I believe the first step would be to restore sda6 so it is visible to Linux.

---

### Post by vlsi on 2009-05-24
OK, everything works and I am officially impressed. I wish one day I can reach your level.:popcorn::KS
Now it is time to study and try to understand your method.
Once again, thank you very much!

---

### Post by unutbu on 2009-05-24
That's great news. Glad I could help. ;)

---

### Post by ugkbunb on 2009-11-23
I have a similiar request... My partition scheme is as follows:

/dev/sdb1 /boot
/dev/sdb2 Extended
/dev/sdb5 /root logical
/dev/sdb6 /home logical
/dev/sdb7 swap logical

I was wondering if it would be possible to make my /root /home + swap all primary primary paritions without loosing any of the data on my drive.

Attached is the output of you asked the original poster to post.

---

### Post by unutbu on 2009-11-24
ugkbunb, I'd be glad to try to help you, but before we embark on this, please know that 
the method is -- or prehaps more accurately, I am -- a bit error prone. As you can see from this thread, it took me a few tries to get it right. 

Changing logical partitions to primary partitions (or vice versa) is justified when there is a partition table error that can not be fixed by more ordinary means (such as GParted or testdisk). But in your case, I don't see why you would want to change logical partitions into primary partitions.

Logical partitions give you more flexibility -- you can have more of them. Since you can only have 4 primary/extended partitions, if you convert /root, /home, /swap into primary partitions, then you won't have an easy way to add more partitions if you so desire at some future date.

So, the first questions is, are you sure you want to do this?

---

### Post by dcstar on 2009-11-24
> **unutbu said:**
> 
.........
Logical partitions give you more flexibility -- you can have more of them. Since you can only have 4 primary/extended partitions, if you convert /root, /home, /swap into primary partitions, then you won't have an easy way to add more partitions if you so desire at some future date.

So, the first questions is, are you sure you want to do this?

Exactly, this is a basically pointless request risking a working system for essentially no benefit whatsoever.

---

### Post by ugkbunb on 2009-11-24
alrighty. I will just leave it as is. Thanks anyways

---

