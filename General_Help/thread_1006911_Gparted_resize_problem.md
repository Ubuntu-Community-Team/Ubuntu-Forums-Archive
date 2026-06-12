---
title: "Gparted resize problem"
date: 2008-12-09
forum: General Help
---

### Post by chenguo4 on 2008-12-09
So I removed my Windows partition, which was 40 gb. I booted up Ubuntu off a thumbstick, and ran gparted.

When I try to move/expand root and home into the now free 40 gb, the operation always says it fails, though randomly gparted's partition table would sometimes change to reflect the changes I made.

So now gparted reads my partitions as what I would like them to be, but my ubuntu reads them as if they were never changed. Also, gparted reports that much more of my partition is used than really is; for example gparted says my /home has 84/99 gb used, while in Ubuntu df -h tells me I'm using 36/51 gb.

Everything is on /dev/sda4, as an extended partition. / and /home are logical partitions on sda4. 

So how would I go about reclaiming this missing hard drive space?

Thanks in advance!

---

### Post by caljohnsmith on 2008-12-10
Are you trying to do the resizing with gparted when you are in your Ubuntu install, or from the Live CD? You should do it from the Live CD so that all your file systems can be unmounted. Another small thing that can cause problems in gparted is you usually have to right-click the swap partition on your HDD and select "swapoff" while in gparted, because the Ubuntu Live CD by default will use any swap partition it finds on the HDD. 

It sounds like at this point your partition table could be corrupt, so how about opening a terminal (Applications > Accessories > Terminal) and please post the full output of:
```
sudo sfdisk -l
sudo fdisk -lu
sudo parted /dev/sda print
```
Next make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen, and we can work from there if you want. :)

---

### Post by chenguo4 on 2008-12-10
Yeah, I ran Ubuntu off my thumbdrive, and used Gparted off that to operate on my actual harddrive. It's just about a live CD, just not on a CD. And yes, I unmounted swap. I learned that lesson firsthand a long time ago.

So here's everything you requested, and I threw in df -h at the end. All of these look right, except df. For what reasons would df not be consistent with these?

```
$ sudo sfdisk -l

Disk /dev/sda: 14593 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0       -       0          0    0  Empty
/dev/sda2          0       -       0          0    0  Empty
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0+  14592   14593- 117218241    5  Extended
/dev/sda5      14430   14592     163    1309297+  82  Linux swap / Solaris
/dev/sda6      14411+  14429      19-    152586   83  Linux
/dev/sda7      14257+  14410     154-   1236973+  83  Linux
/dev/sda8       1305+  14256   12952- 104036908+  83  Linux
/dev/sda9          0+   1304    1305-  10482318   83  Linux



$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x16351635

   Device Boot      Start         End      Blocks   Id  System
/dev/sda4              63   234436544   117218241    5  Extended
/dev/sda5       231817950   234436544     1309297+  82  Linux swap / Solaris
/dev/sda6       231512778   231817949      152586   83  Linux
/dev/sda7       229038768   231512714     1236973+  83  Linux
/dev/sda8        20964888   229038704   104036908+  83  Linux
/dev/sda9             189    20964824    10482318   83  Linux

Partition table entries are not in disk order





$ sudo parted /dev/sda print
Model: ATA FUJITSU MHV2120A (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 4      32.3kB  120GB   120GB   extended                    
 9      96.8kB  10.7GB  10.7GB  logical   ext3              
 8      10.7GB  117GB   107GB   logical   ext3              
 7      117GB   119GB   1267MB  logical   ext3              
 6      119GB   119GB   156MB   logical   ext3              
 5      119GB   120GB   1341MB  logical   linux-swap       
``` 




This is from testdisk
```
Disk /dev/sda - 120 GB / 111 GiB - CHS 14594 255 63
     Partition               Start        End    Size in sectors
D Linux                    0   3  1  1245 254 63   20016801 [/]
D Linux                 1305   1  1  7956 254 63  106864317 [/home]
D Linux                 7957   1  1  8110 254 63    2473947
D Linux                 8111   1  1  8129 254 63     305172
D Linux Swap            8130   0  1  8292 254 63    2618595
D FAT32 LBA             8293   1  1  9952 254 63   26667837 [HP_RECOVERY]
D Linux                12466   1  1 12619 254 63    2473947
D Linux                12620   1  1 12638 254 63     305172
D Linux Swap           12639   0  1 12801 254 63    2618595
D FAT32 LBA            12802   1  1 14461 254 63   26667837 [HP_RECOVERY
```]

Interestingly, everything here shows up as D for deleted... And the HP_RECOVERY is left over from my deleted windows partition.



Just for reference, this is df -h. This seems to be consistent with what system monitor's file systems tab tells me.
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda9             9.5G  3.5G  5.5G  39% /
tmpfs                 505M     0  505M   0% /lib/init/rw
varrun                505M  228K  504M   1% /var/run
varlock               505M     0  505M   0% /var/lock
udev                  505M  2.8M  502M   1% /dev
tmpfs                 505M  692K  504M   1% /dev/shm
lrm                   505M  2.0M  503M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sda6             145M   48M   90M  35% /boot
/dev/sda8              51G   37G   12G  76% /home
/dev/sda7             1.2G  887M  252M  78% /var
```

---

### Post by caljohnsmith on 2008-12-10
> ```
$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x16351635

Device Boot Start End Blocks Id System
/dev/sda4 63 234436544 117218241 5 Extended
/dev/sda5 [COLOR="Red"]231817950[/COLOR] 234436544 1309297+ 82 Linux swap / Solaris
/dev/sda6 231512778 [COLOR="Red"]231817949[/COLOR] 152586 83 Linux
/dev/sda7 229038768 231512714 1236973+ 83 Linux
/dev/sda8 20964888 229038704 104036908+ 83 Linux
/dev/sda9 189 20964824 10482318 83 Linux
```
I believe I see a problem with your partition table above; your sda6 partition ends on the sector immediately before the starting sector of sda5. Since those are logical partitions, they must be separated by a minimum of 64 sectors, just like the rest of your logical partitions are. I would try deleting your swap partition and then recreating it with gparted, and afterwards post the new output of:
```
sudo fdisk -lu
```
Fixing the swap partition starting sector should at least get you closer to solving your problem, although your problem with the sda8 /home partition could be entirely unrelated. Also, the swap partition UUID will change when you recreate it, so to change the UUID back to what it was originally, just do the following once you boot back into Ubuntu:
```
sudo swapoff -a
sudo mkswap -U $(awk -F"=" '{print $3}' /etc/initramfs-tools/conf.d/resume) /dev/[COLOR="Blue"]sda5[/COLOR]
sudo swapon /dev/[COLOR="Blue"]sda5[/COLOR]

```
And change "sda5" above if for some reason the new swap partition has a different number. Let me know how it goes.

---

### Post by chenguo4 on 2008-12-10
Erm... Problem. I'm getting Grub error 15 when I turn on my computer. I'm typing this  from YDL on my PS3.

When I deleted my swap, everything else moved up 1 number, so sda6 became sda5, sda7 became sda6, etc etc. And when I recreated my swap, it became sda9. 

I'm thinking I can edit some grub config files to let grub know of the changes... I thought it'd be menu.lst and did a quick runthrough of it, but found nothing. So what should I edit to let grub know?

Thanks.

---

### Post by caljohnsmith on 2008-12-10
OK, how about first doing:
```
sudo grub
grub> root (hd0,4)
grub> setup (hd0)
grub> quit
```
And please post the output of the above commands. Next make sure your fstab uses UUIDs so that it is OK:
```
sudo mount /dev/sda8 /mnt
sudo blkid
gksudo gedit /mnt/etc/fstab &
```
Then compare the lines in your fstab with the UUIDs given by the blkid command, and make sure they agree. If so, reboot and see how far you get, and we can work from there.

---

### Post by chenguo4 on 2008-12-10
Ok I can't copy paste from the my computer to the ps3 (thumbstick's internet doesn't work, needs fwcutter), so excuse the spacing and any typos.

setup (hd0) tells me:
Checking if "/boot/grub/stage1" exists... no
Checking if "/grub/stage1" exists... yes
Checking if "/grub/stage2" exists... yes
Checking if "/grub/e2fs_stage1_5" exists... yes
Running "embed /grub/e2fs_stage1_5 (hd0)"... 16 sectores are embedded.
succeeded
Running "install /grub/stage1 (hd0) (hd0)1+16 p (hd0,4)/grub/menu.lst"... succeeded
Done.


And in cases where blkid and fstab dont agree, I'm editing fstab to match blkid. Gonna see if I can boot... Thanks a lot.

---

### Post by chenguo4 on 2008-12-10
Well, error 15 still comes up, but now it's delayed.

Before, error 15 would pop up after the 2 lines of grub loading. Now error 15 occurs after a screen refresh. So I'm assuming, grub's there now, but it can't find my hard drive?

My menu.lst says hd0,5. I'm gonna change that to 4 and see what happens.


edit: ok I can boot now. So now we're back to square one, my home is still 36/50 gb when it should be 36/100 gb. Any other ideas?

---

### Post by caljohnsmith on 2008-12-10
How about from the Live CD, and while your home partition isn't mounted, try:
```
sudo fsck -y /dev/sda7
```
And replace sda7 with whatever the home partition is now if it is different. After that, boot into Ubuntu and please post the output of:
```
sudo fdisk -lu
df -h
```
And we can work from there.

---

### Post by chenguo4 on 2008-12-11
So just to make sure, though I'm not mounting home, I'm mounting root, correct? I'm talking about for fsck.

Also, I'm wondering... When testdisk ran analysis, and marked all my partitions with a D which it said meant they were deleted, that's not normal, is it?

---

### Post by caljohnsmith on 2008-12-11
> **chenguo4 said:**
> So just to make sure, though I'm not mounting home, I'm mounting root, correct? I'm talking about for fsck.

Also, I'm wondering... When testdisk ran analysis, and marked all my partitions with a D which it said meant they were deleted, that's not normal, is it?
If you run the fsck from the Live CD, you don't need to have your root partition mounted either. The main thing is not to have whichever partition mounted that you run an fsck on, so to run an fsck on your home partition, then the home partition shouldn't be mounted. And about testdisk, it simply lists all the possible partitions that it can find on the HDD and arbitrarily marks them as "D", "P", "L", etc, but that doesn't mean the partitions are actually deleted; you can select each partition that testdisk lists and change it from "D" to "P" or "L" for example, but it has no effect until you actually use testdisk to write a new partition table.

---

### Post by chenguo4 on 2008-12-11
K,thanks for clearing the testdisk thing up.

So I ran fsck like you said. Is it supposed to be like an almost instantaneous operation? From my experience anything dealing with a 100 gb chunk of data doesn't take an instant, but fsck spit out 2 lines to stdout in like a tenth of a second and was done.

In any case, here's my fdisk and df output:

```

$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x16351635

   Device Boot      Start         End      Blocks   Id  System
/dev/sda4              63   234436544   117218241    5  Extended
/dev/sda5       231512778   231817949      152586   83  Linux
/dev/sda6       229038768   231512714     1236973+  83  Linux
/dev/sda7        20964888   229038704   104036908+  83  Linux
/dev/sda8             189    20964824    10482318   83  Linux
/dev/sda9       231818013   234436544     1309266   82  Linux swap / Solaris

Partition table entries are not in disk order


$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda8             9.5G  3.5G  5.5G  39% /
tmpfs                 505M     0  505M   0% /lib/init/rw
varrun                505M  216K  504M   1% /var/run
varlock               505M     0  505M   0% /var/lock
udev                  505M  2.8M  502M   1% /dev
tmpfs                 505M  876K  504M   1% /dev/shm
lrm                   505M  2.0M  503M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sda5             145M   48M   90M  35% /boot
/dev/sda7              51G   39G  9.3G  81% /home
/dev/sda6             1.2G  892M  247M  79% /var


```

My home's still marked as 51 gb.

---

### Post by caljohnsmith on 2008-12-11
> **chenguo4 said:**
> K,thanks for clearing the testdisk thing up.

So I ran fsck like you said. Is it supposed to be like an almost instantaneous operation? From my experience anything dealing with a 100 gb chunk of data doesn't take an instant, but fsck spit out 2 lines to stdout in like a tenth of a second and was done.

That's definitely not a good sign, because as you say, fsck should take a while to do its check. What exactly was the output of fsck? it sounds like the file system of your home partition could be partially corrupt because of the failed partition resizing. Maybe you should consider copying the contents of your sda7 home partition to another drive, and then reformat that partition. If that works and df shows the partition is 104 GB instead of 51 GB, then I think it would be safe to use the partition; but if df still shows 51 GB, I would delete the partition altogether and recreate it. I think formatting the partition should be enough though. Let me know what you decide to do.

---

### Post by chenguo4 on 2008-12-13
I really might just copy my /home to an external and just reformat the entire hard drive.

On a positive note, however, I ran gparted again to save the error output. I shrunk my home parititon by like 20 mb and now df actually reads it as 99 gb. However, I tried the same with / and df still insists it's 9.5 gb, and not 10. It almost seems like it's up to pure random luck... Anyhow, I might just try this a couple of times and see if eventually / will come around too, but that's just 500 mb so it's not a huge deal.

And yeah, worse case scenario, if it really bugs me, I'll just reformat everything, which should take care of all problems. 

Thanks so much for all the help.

---

### Post by caljohnsmith on 2008-12-13
That's interesting that resizing /home by a small amount seems to have fixed the problem of getting it recognized as 99 GB. I hope you haven't unintentionally found a bug with gparted. Maybe it's safe to keep things as they are, but if you run into more related problems, I think your idea of copying off your data and reformatting is a good one. :)

---

