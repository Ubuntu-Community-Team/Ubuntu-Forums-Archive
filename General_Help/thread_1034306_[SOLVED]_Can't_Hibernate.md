---
title: "[SOLVED] Can't Hibernate"
date: 2009-01-08
forum: General Help
---

### Post by theozzlives on 2009-01-08
I try to hibernate, the screen goes blank, says something about cannot allocate memory, then asks my password and WEP key. The system load average goes to 100% and slowly goes back down. I have a 2 GB swap (same as my RAM).

---

### Post by drs305 on 2009-01-08
First you want to check to see if swap is enabled. If it is, you should see some values for swap with the following command. If swap is not enabled, you will see all zeroes.
```
free -m
```
Typical results would be something like:
```

$: free -m
             total       used       free     shared    buffers     cached
Mem:          3959       2984        975          0       1365        781
-/+ buffers/cache:        837       3122
[COLOR="DarkRed"]**Swap:         4102          0       4102**[/COLOR]

```

If it shows all zeros, you should be able to turn it on with "sudo swapon -a".

 you can search these forums for swap issues or report back. Often the issue is an improper UUID in either fstab or in /etc/initramfs-tools/conf.d/resume

---

### Post by theozzlives on 2009-01-08
```
             total       used       free     shared    buffers     cached
Mem:          2014        478       1535          0         18        181
-/+ buffers/cache:        279       1735
Swap:          503          0        503
o
```

I have a 2 GB swap, why's it say  503?

---

### Post by drs305 on 2009-01-08
Run the following and take a look at your swap partition:
```
sudo fdisk -l
```

---

### Post by theozzlives on 2009-01-08
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1305    10482381   83  Linux
/dev/sda2            1306       15633   115089660   83  Linux
/dev/sda3   *       15634       19196    28619797+   7  HPFS/NTFS
/dev/sda4           19197       19457     2096482+   5  Extended
/dev/sda5           19197       19457     2096451   82  Linux swap / Solaris

---

### Post by unutbu on 2009-01-08
Please post the output of
```

swapon -s
cat /etc/fstab
```

The first command should show something like this:
```
Filename				Type		Size	Used	Priority
/dev/sda5                               partition	2096443	0	-1
```
It would be interesting if it reports something less for the size.

---

### Post by theozzlives on 2009-01-08
I increased my swap to 4 GB:
```
ozzie@ozzie-laptop:~$ free  -m
             total       used       free     shared    buffers     cached
Mem:          2014        552       1462          0         22        187
-/+ buffers/cache:        343       1671
Swap:         4598          0       4597
ozzie@ozzie-laptop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1305    10482381   83  Linux
/dev/sda2            1306       15633   115089660   83  Linux
/dev/sda3   *       15634       18935    26523315    7  HPFS/NTFS
/dev/sda4           18936       19457     4192965    5  Extended
/dev/sda5           18936       19457     4192933+  82  Linux swap / Solaris

```

Still can't hibernate

---

### Post by theozzlives on 2009-01-08
> **unutbu said:**
> Please post the output of
```

swapon -s
cat /etc/fstab
```

The first command should show something like this:
```
Filename				Type		Size	Used	Priority
/dev/sda5                               partition	2096443	0	-1
```
It would be interesting if it reports something less for the size.

sorry didn't see that request for data:
```
ozzie@ozzie-laptop:~$ swapon -s
Filename				Type		Size	Used	Priority
/dev/ramzswap0                          partition	515796	0	100
/dev/sda5                               partition	4192924	0	-1
ozzie@ozzie-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b37ac976-2337-487e-a1ed-80e7a6edf077 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
/dev/sda2 /home ext3 nodev,nosuid 0 2
# Windows Partition
/dev/sda3 /windows ntfs 0 0
# DVD Writer
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by theozzlives on 2009-01-08
Bump, you know I lost 4 GB hard drive space trying to hibernate. Someone please help.

---

### Post by unutbu on 2009-01-08
Type
```

blkid
```

Look for the line in the output that says TYPE="swap":
```

/dev/sda5: TYPE="swap" UUID="bcbf2c68-7c2d-4e9d-bf4b-bdc6f3ee74c5" 
```

Note the UUID. Then edit /etc/fstab:
```

gksu gedit /etc/fstab
```

Add these two lines:
```

# /dev/sda5
UUID=bcbf2c68-7c2d-4e9d-bf4b-bdc6f3ee74c5 none            swap    sw              0       
```

Change "bcbf2c68-7c2d-4e9d-bf4b-bdc6f3ee74c5" to the correct UUID for your swap partition. 

By editing fstab in this way, your machine will use your sda5 partition as a swap partition at boot.

Still using gedit, open /etc/initramfs-tools/conf.d/resume.

Make sure, and/or change the contents of that file to:
```

RESUME=UUID=bcbf2c68-7c2d-4e9d-bf4b-bdc6f3ee74c5
```

Once again changing the UUID to the correct UUID for your swap partition.

Save both /etc/fstab and /etc/initramfs-tools/conf.d/resume and then try to hibernate.

---

### Post by theozzlives on 2009-01-08
ozzie@ozzie-laptop:~$ blkid
/dev/sda1: UUID="b37ac976-2337-487e-a1ed-80e7a6edf077" TYPE="ext3" 
/dev/sda2: UUID="bbe88f91-aa3a-4d91-bcab-9d704608421a" TYPE="ext3" 
/dev/sda3: UUID="FE3884CD3884867D" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 
ozzie@ozzie-laptop:~$

---

### Post by theozzlives on 2009-01-08
/dev/sda1: UUID="b37ac976-2337-487e-a1ed-80e7a6edf077" TYPE="ext3" 
/dev/sda2: UUID="bbe88f91-aa3a-4d91-bcab-9d704608421a" TYPE="ext3" 
/dev/sda3: UUID="FE3884CD3884867D" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs"

---

### Post by pizpot on 2009-01-08
(moderator please delete this accidental post)

---

### Post by unutbu on 2009-01-08
theozzlives, sometimes the cache that blkid reads is not updated if you've just created the swap partition sda5. In this case, type
```

sudo vol_id /dev/sda5
```

Look for a line that looks like this:
```

ID_FS_UUID=03a507ee-cdac-4bd9-b438-eccd616b66ed
```

This will tell you the UUID of /dev/sda5.
[B]
--------------------------------------------------------------------------------------------------------
[/B]
pizpot, to disable hibernation, open a terminal and type
```

gconf-editor
```

A window will open. In the left panel, click on apps>gnome-power-manager>general>can_hibernate. Disable the checkbox. You can also disable suspend this way if you wish.

Close gconf-editor. Log out and then log back in. The option to hibernate should now be gone. 

When you log out however, the (GDM) login screen has an options menu in the lower left corner which also allows you to restart, shutdown, hibernate and suspend. To remove hibernation as an option from the GDM login screen, 
```

gksu gedit /etc/gdm/gdm.conf
```

Search and remove "HIBERNATE;" from these two lines:
```

SystemCommandsInMenu=HALT;REBOOT;HIBERNATE;SUSPEND;CUSTOM_CMD
```
```

AllowLogoutActions=HALT;REBOOT;HIBERNATE;SUSPEND;CUSTOM_CMD
```

---

### Post by theozzlives on 2009-01-09
I'm close here's my settings now:
```
ozzie@ozzie-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2014        892       1122          0         61        291
-/+ buffers/cache:        538       1476
Swap:         4598          4       4593
ozzie@ozzie-laptop:~$ sudo fdisk -l
[sudo] password for ozzie: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1305    10482381   83  Linux
/dev/sda2            1306       15633   115089660   83  Linux
/dev/sda3   *       15634       18935    26523315    7  HPFS/NTFS
/dev/sda4           18936       19457     4192965    5  Extended
/dev/sda5           18936       19457     4192933+  82  Linux swap / Solaris
ozzie@ozzie-laptop:~$ swapon -s
Filename				Type		Size	Used	Priority
/dev/ramzswap0                          partition	515796	4960	100
/dev/sda5                               partition	4192924	0	-1
ozzie@ozzie-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b37ac976-2337-487e-a1ed-80e7a6edf077 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
/dev/sda2 /home ext3 nodev,nosuid 0 2
# Windows Partition
/dev/sda3 /windows ntfs 0 0
# /dev/sda5
UUID=351ea5ea-d808-494d-9d40-c067e9dcb59d none            swap    sw              0
# DVD Writer
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

ozzie@ozzie-laptop:~$ blkid
/dev/sda1: UUID="b37ac976-2337-487e-a1ed-80e7a6edf077" TYPE="ext3" 
/dev/sda2: UUID="bbe88f91-aa3a-4d91-bcab-9d704608421a" TYPE="ext3" 
/dev/sda3: UUID="FE3884CD3884867D" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 
/dev/ramzswap0: TYPE="swap" 
/dev/sda5: UUID="351ea5ea-d808-494d-9d40-c067e9dcb59d" TYPE="swap" 
ozzie@ozzie-laptop:~$ 


```

It says error reading swap and exits

---

### Post by theozzlives on 2009-01-09
bump

---

### Post by theozzlives on 2009-01-09
I think my problem is my ramzswap is at 100 and my swap is -1, I shouldn't have ramzswap should I?

---

### Post by unutbu on 2009-01-09
To change the priority of the swap devices, type:
```

sudo swapoff /dev/ramzswap0
sudo swapoff /dev/sda5
sudo swapon -p -1 /dev/sda5
sudo swapon -p -2 /dev/ramzswap0
swapon -s  # To check that the change worked

```
Once you get the priority of sda5 higher than the priority of ramzswap0, try hibernating again. Hopefully it will work.

If it doesn't work, please post 
```

cat /var/log/pm-suspend.log
```

---

