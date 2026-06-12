---
title: "Partition not recognized in diskpart"
date: 2009-04-29
forum: General Help
---

### Post by jubop on 2009-04-29
I'm trying to install vista as a dual boot on my laptop (lenovo 3000 N100), following these instructions:

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=4](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=4)

I can get as far as choosing which driver/partition to put windows on, but when I open an administrator window (shift+F10) and enter diskpart to list partitions and activate the new one, the new parition I made for windows isn't listed, but the windows vista CD recognizes the new partition (as it should) and can't download to it (obviously cuz it's not been actviated). So basically how can I get it recognized in diskpart? This is what diskpart lists:

Partition         Type          Size     Offset
Partition 1       Primary       1906 Mb  32 Kb
Partition 0       Extended        73 Gb  1906 Mb
Partition 2       Logical         42 Gb  32   Gb

The partition I made for vista is 32 Gb, ubuntu's on parition 2. Sorry is this info is useless I'm not the most advanced computer user.

Also let me know If the partitions aren't good (like the size), If it would be easier to just completely reinstall both ubuntu and windows I wouldn't mind as I've backed up any of the files I need to a flashdrive.

Thanks in advance for any help and let me know if anyone requires more info to help me.

---

### Post by jubop on 2009-04-29
I think the issue is that the new partition has become an extended partition and so diskpart is only recognizing it as free space on the drive and not an actual partition. I beleive I have to make it into a primary partition?

---

### Post by caljohnsmith on 2009-04-30
In order to help clarify your current partition setup, how about booting a Linux Live CD, open a terminal, and please post the output of:
```
sudo fdisk -lu

```
Or if you have Ubuntu or some other linux distro all ready installed on that HDD, you could boot into it and run that command. Anyway, that will help clarify your partitioning scheme, and we can work from there if you want. :)

Cheers,
John

---

### Post by stovepilot on 2009-07-17
I have exactly the same problem as the original poster.  Can anyone help?  The results of fdisk -lu are:

sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x60000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   414830429   207415183+  83  Linux
/dev/sda2       476262990   488392064     6064537+   5  Extended
/dev/sda5       476263053   488392064     6064506   82  Linux swap / Solaris

I'd be grateful for any help,

Tom

---

### Post by merlinus on 2009-07-17
In order to install vista you will have to shrink sda1 and create an ntfs partition in the freed-up space to make room for it.  You can use gparted on the live cd to do this.

Windows will not recognize linux partitions.

---

### Post by stovepilot on 2009-07-17
Fixed it

On the installation location screen in Vista click on New.  Then hit SHFIT and F10 again, type diskpart and then list partition.  The newly created partition will then be visible.  Select it, activate it then exit:

select partition n
active
exit

Back on the location selection screen select the partition and click format.  Then continue with the installation.

---

