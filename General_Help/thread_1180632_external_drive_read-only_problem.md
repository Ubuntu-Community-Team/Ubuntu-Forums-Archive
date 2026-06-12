---
title: "external drive read-only problem"
date: 2009-06-07
forum: General Help
---

### Post by MeanStreak on 2009-06-07
Hi

Basically I'm trying to transfer the contents of my Home directory to another computer via external HDD.

Ubuntu recognises when my external drive is connected via USB, but I cannot write to the drive, i.e. Ubuntu registers the drive as read-only. 

I raised this issue in another post ([http://ubuntuforums.org/showthread.php?t=1173578](http://ubuntuforums.org/showthread.php?t=1173578)) but still have no successful resolution. I even formatted my external drive, changing from FAT32 to Ext3 without success. I have even tried another external drive and experienced the same problem.

Could someone please provide a fix? Happy to provide additional information if required. This is quickly becoming a critical issue as I now have no backup. :(

cheers,

meanstreak

---

### Post by merlinus on 2009-06-07
When you plug in the drive, is it visible in nautilus?

---

### Post by vikkikanhaua on 2009-06-07
this might be a problem of permissions
find out the permissions of your hdd by checking the output of "ls -l" on the mountpoint of hdd or its folder properties.

---

### Post by MeanStreak on 2009-06-07
> **merlinus said:**
> When you plug in the drive, is it visible in nautilus?

Yes, visible in Nautilus and Dolphin.

---

### Post by MeanStreak on 2009-06-07
> **vikkikanhaua said:**
> this might be a problem of permissions
find out the permissions of your hdd by checking the output of "ls -l" on the mountpoint of hdd or its folder properties.

The external drive is called 'My Passport' - see below:
```

charles@charles-desktop:~$ cd ..
charles@charles-desktop:/home$ cd ..
charles@charles-desktop:/$ ls
bin    etc         initrd.img.old  mnt   sbin     tmp      vmlinuz.old
boot   home        lib             opt   selinux  usr
cdrom  initrd      lost+found      proc  srv      var
dev    initrd.img  media           root  sys      vmlinuz
charles@charles-desktop:/$ cd media
charles@charles-desktop:/media$ ls
cdrom  cdrom0  floppy  floppy0  My Passport  sda1
charles@charles-desktop:/media$ cd My Passport
bash: cd: My: No such file or directory
charles@charles-desktop:/media$ 
```

However, navigating to the drive seems less than trivial.

---

### Post by merlinus on 2009-06-07
```

gksudo nautilus

```will open nautilus as root.  Perhaps you can then change the permissions by right-clicking on the drive, selecting properties, and then permissions?

---

### Post by MeanStreak on 2009-06-07
> **merlinus said:**
> ```

gksudo nautilus

```

will open nautilus as root.  Perhaps you can then change the permissions by right-clicking on the drive?

Thanks. I opened nautilus as root and accessed permissions by right-clicking in the top-level directory of the drive. However changing the permissions was not possible - see screenshots.

---

### Post by MeanStreak on 2009-06-07
> **MeanStreak said:**
> Thanks. I opened nautilus as root and accessed permissions by right-clicking in the top-level directory of the drive. However changing the permissions was not possible - see screenshots.

Also, the command shell gave me this feedback:
```
charles@charles-desktop:~$ gksudo nautilus

** (nautilus:4895): WARNING **: Unable to add monitor: Operation not supported
e' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory

(nautilus:4895): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

--- Hash table keys for warning below:
--> file:///root
--> file:///media/My%20Passport
--> file:///root/Desktop

(nautilus:4895): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 3 elements at quit time (keys above)

(nautilus:4895): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 3 elements at quit time
charles@charles-desktop:~$ 


```

---

### Post by MeanStreak on 2009-06-07
Is anyone able to help? I'm really lost here. I cannot move any of my files or back up any of my files to either of my two WD external hard drives.

---

### Post by merlinus on 2009-06-07
Can you rename the drive without spaces, e.g. My_Passport?  A long shot, yes, but at this point, who knows?

---

### Post by MeanStreak on 2009-06-07
> **merlinus said:**
> Can you rename the drive without spaces, e.g. My_Passport?  A long shot, yes, but at this point, who knows?

Yes, good idea. I tried that however and did not have permission, even when using Nautilus under sudo.

---

### Post by merlinus on 2009-06-07
So it is still read-only, even with the name change?

If so, the only other thing I can think of is to try and partition it using gparted, which you may have to run from the live cd.

---

### Post by MeanStreak on 2009-06-07
> **merlinus said:**
> So it is still read-only, even with the name change?

If so, the only other thing I can think of is to try and partition it using gparted, which you may have to run from the live cd.

My apologies - the name change was not successfully applied.

I have formatted the entire disc to both FAT32 and EXT3 formats with no success either. I have also tried another external drive and no luck either. External thumb drive is accepted however. 

This seems to be a serious bug with the Ubuntu mounting system, as opposed to some basic permission-based problem or even a problem with the drives.

---

### Post by merlinus on 2009-06-07
With the drive plugged in, run these commands in a terminal and post results:

```

sudo fdisk -l
mount

```l is a lowercase L

It also may be necessary to create a mountpoint for the drive in order to write to it.

---

### Post by merlinus on 2009-06-07
This info may be of assistance:

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

### Post by jeromedavies on 2009-06-07
I found this reference to My Passport problems it relates to the power requirements of the drive. (The link relates to a PowerBook / MacBook). I wonder if this is a related problem.


[http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=1497&p_created=1169159903&p_sid=67AIkTWi&p_accessibility=0&p_redirect=&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MjM1LDIzNSZwX3Byb2RzPSZwX2NhdHM9JnBfcHY9JnBfY3Y9JnBfc2VhcmNoX3R5cGU9c2VhcmNoX2ZubCZwX3BhZ2U9MSZwX3NlYXJjaF90ZXh0PXBhc3Nwb3J0IG5vdCBtb3VudGVk&p_li=&p_topview=1](http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=1497&p_created=1169159903&p_sid=67AIkTWi&p_accessibility=0&p_redirect=&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MjM1LDIzNSZwX3Byb2RzPSZwX2NhdHM9JnBfcHY9JnBfY3Y9JnBfc2VhcmNoX3R5cGU9c2VhcmNoX2ZubCZwX3BhZ2U9MSZwX3NlYXJjaF90ZXh0PXBhc3Nwb3J0IG5vdCBtb3VudGVk&p_li=&p_topview=1)

---

### Post by MeanStreak on 2009-06-07
> **merlinus said:**
> With the drive plugged in, run these commands in a terminal and post results:

```

sudo fdisk -l
mount

```l is a lowercase L

It also may be necessary to create a mountpoint for the drive in order to write to it.

Output of sudo fdisk -l:
 
```
charles@charles-desktop:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfc6ffc6f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5737    46082421    b  W95 FAT32
/dev/sda2            5738       14341    69111630   83  Linux
/dev/sda3           14342       14593     2024190    5  Extended
/dev/sda5           14342       14593     2024158+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4076f59e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       13419   107788086   83  Linux
/dev/sdb2           13420       19457    48500235    b  W95 FAT32

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table
charles@charles-desktop:~$ 
```

Output of mount:

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfc6ffc6f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5737    46082421    b  W95 FAT32
/dev/sda2            5738       14341    69111630   83  Linux
/dev/sda3           14342       14593     2024190    5  Extended
/dev/sda5           14342       14593     2024158+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4076f59e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       13419   107788086   83  Linux
/dev/sdb2           13420       19457    48500235    b  W95 FAT32

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table
charles@charles-desktop:~$ mount
/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
/dev/sdb1 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/charles/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=charles)
/dev/sdb2 on /media/CharlesDocs type vfat (rw)
charles@charles-desktop:~$ mount
/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
/dev/sdb1 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/charles/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=charles)
/dev/sdb2 on /media/CharlesDocs type vfat (rw)
charles@charles-desktop:~$ 

```

---

### Post by MeanStreak on 2009-06-07
I've even tried the internal route - formatting a partition of my drive to FAT32 (my destination is a non-linux based OS) - I thought this would surely work, but then when I tried to copy my docs over - bang - no write permission to even an internal drive on my machine. This is beyond ridiculous. Ubuntu has bought me to a total stand still.

---

### Post by merlinus on 2009-06-07
Linux uses partitions on hdds, and they have to be mounted to be used.  This is the way it works.  End of story.

So you can use gparted to create partitions on your external drive, and then mount them.  The link I provided gives information about this, not only about changing drive names.

The relevant info from the terminal commands is:

Disk /dev/sdc doesn't contain a valid partition table

You can also view the filesystems and mountpoints for the partitions on your first and second hdds within the information provided by the commands.

---

