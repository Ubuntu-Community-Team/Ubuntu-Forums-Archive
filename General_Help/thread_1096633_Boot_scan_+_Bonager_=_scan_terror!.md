---
title: "Boot scan + Bonager = scan terror!"
date: 2009-03-15
forum: General Help
---

### Post by Thanh-BKK on 2009-03-15
Hi.

Minor issue, but i'd like to find a solution to it because after lots of googling i didn't find it.

So there's this "routine disc check" that comes up every so often. Then there's this application "Bonager" which shows when the next scan is due and it allows to postpone such scan.

HOWEVER my Ubuntu (8.04.1, kernel 2.6.24-23 generic) does not stick to the schedules and scans whenever it feels like it! The "norm" as my googling found should be every 30 days, but mine does it (and Bonager verifies that these are indeed scheduled scans) after 20, 18, 16, 11 or even 5 days. 

And EVERY time Bonager comes up with "scan scheduled for next boot, postpone now?" i click "no" but regardless the scan does NOT happen that next boot, instead the same message comes up with the addition "you have postponed once already..." which is simply BS as i did NOT postpone it.

Next boot after that i will finally do the scan.

Now HOW can i train Ubuntu to stick to a fixed schedule, like every 30 days as it should..??

By the way there are never any errors but sometimes i just want to get my computer up and running in the early morning and don't want to wait for that scan to be completed, at least not as often as it does it now.

Many thanks in advance for any tricks and solutions :)

Kind regards......

Thanh

PS when i wrote "days" i mean "boots" as i have to shut down the computer over night, i.e. i boot it every morning.

---

### Post by plucky on 2009-03-15
Look at ```
man tune2fs
``` to change the max_count value on a partition.


Good luck

---

### Post by Thanh-BKK on 2009-03-15
Hi :)

Thank you very much for that. However this large chunk of information confuses me more than it actually helps - i see that i have an awful lot of options there but each and every one of them appears to have the ability to screw up my file system?? That is NOT what i am trying to do :)

Could you (or anyone) give me a very simple and fool-proof instruction on

1) how to check for the current settings (which seem to be variable?)
2) how to change it to a specific interval such as "every 30 boots"

Many thanks in advance :)

Kind regards......

Thanh

---

### Post by plucky on 2009-03-15
First list your partitions with ```
sudo fdisk -l
```
Then list the contents of the filesystem superblock with ```
sudo tune2fs -l /dev/sdaX
``` where l=lowercase L and X=a partition number.


Then to change the mount count for a particular partition,use ```
sudo tune2fs -c 35 /dev/sdaX
``` should change the max_mount_count to 35 for partition /dev/sdaX


Good Luck

---

### Post by Hobgoblin on 2009-03-15
> **Thanh-BKK said:**
> The "norm" as my googling found should be every 30 days, 

Every 30 **mounts**, normally a filesystem will be mounted once each time you start or restart the system, if you do 60 restarts in a day then on 2 of them it will want to do a check.

---

### Post by Thanh-BKK on 2009-03-15
Hello :)

Thanks again for the replies. I have done this and got the following:

[B]Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000756cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3948    31712278+  83  Linux
/dev/sda2            3949        9729    46435882+   5  Extended
/dev/sda5            3949        4457     4088511   82  Linux swap / Solaris
/dev/sda6            4458        9729    42347308+  83  Linux
[/B]

I then proceeded with the second command on /dev/sda1 and it worked ok, got me the following:

[B]Check interval:           15552000 (6 months)
Next check after:         Wed Sep  9 05:25:44 2009[/B]

HOWEVER trying it on the next two partitions/volumes it kind of failed:

[B]thanh@thanh-desktop:~$ sudo tune2fs -l /dev/sda2
tune2fs 1.40.8 (13-Mar-2008)
tune2fs: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda2
Couldn't find valid filesystem superblock.[/B]

[B]thanh@thanh-desktop:~$ sudo tune2fs -l /dev/sda5
tune2fs 1.40.8 (13-Mar-2008)
tune2fs: Bad magic number in super-block while trying to open /dev/sda5
Couldn't find valid filesystem superblock.[/B]

Last one then once again worked:

[B]Mount count:              26
Maximum mount count:      29[/B]

So now i'll wait for a couple of days when the next scan is due to see which ones it actually checks all the time, but i do believe it is the two with the strange messages (it's always two partitions). 

My system behaves, apart from these scans, without any errors..... so do i need to take action on those "errors" or not? That "Bad Magic Number" sounds not good to me, but do i need to do anything about it, and if so, how?

Many thanks in advance......

Thanh

---

### Post by plucky on 2009-03-16
> /dev/sda2 3949 9729 46435882+ 5 Extended
/dev/sda5 3949 4457 4088511 82 Linux swap / Solaris


Those two partitions will not be checked by fsck at startup as sda2 is the wrapper for the extended partition and the swap partition should not be checked as it should have a 0 at the end of the line in fstab. e.g. ```
UUID=3098bbfe-baae-4aa7-8a06-fb0431b51358  none            swap    sw              0       [color=red]0[/color]
```

Post the output of your fstab file ```
cat /etc/fstab
```

---

### Post by Thanh-BKK on 2009-03-16
Hi :)

Thank you again :) Here comes my fstab:

[B]thanh@thanh-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=50c08996-facc-4c92-928e-82a2baa4bedc / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda6 :
UUID=9a5687d4-3ba5-4c6d-aba4-1d9bcb68f42b /home ext3 relatime 0 2
[COLOR="Red"]# Entry for /dev/sda5 :
UUID=14926b8f-7a88-4b5a-add9-80adca4d0280 none swap sw 0 0[/COLOR]
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sdb5 /media/U-Torrent ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdb3 /media/Backup ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdb2 /media/Music ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdb1 /media/Data ntfs-3g defaults,locale=en_US.UTF-8 0 0
[/B]

Appears to be just like you said, with the zero in the end. Those NTFS partitions btw. are a second physical HDD, they also came up before however i didn't put that information here as those are NOT scanned at boot, it's always two of the "sda" partitions. 

According to Bonager i have now still "2 mounts until next scan", the same it told me yesterday (and the computer was off during the night as always). Or is Bonager itself the problem here? But me don't think so because my reason for installing that was my confusion over the rather unregular and much too many boot scans....

Kind regards.....

Thanh

---

