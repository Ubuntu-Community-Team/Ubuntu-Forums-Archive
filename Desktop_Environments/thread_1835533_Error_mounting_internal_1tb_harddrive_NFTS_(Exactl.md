---
title: "Error mounting internal 1tb harddrive NFTS (Exactly the same size as install HD)"
date: 2011-08-29
forum: Desktop Environments
---

### Post by JamboBuenna on 2011-08-29
<First post so apologies if I make a few mistakes on forum convention>

I am attempting to access my 3rd harddrive on a fresh install of Ubuntu (11.04)  and after not being able to mount through the GUI I tried using the Disk Utility program. Upon selecting and specifying the drive to mount this threw the error.

Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sdb1 is already mounted on /
mount failed

Whilst a quick google search brought me to the ubuntu forums, I was unable to idenitfy how to fix this problem from the results.

The harddrive I am trying to Mount is 1tb and is called Films, whilst the other two are named Main Install and TV.

From terminal commands...

sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00093f20

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121601   976760001    7  HPFS/NTFS

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc5b57adc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      243202  1953512448    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003a885

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      121080   972567552   83  Linux
/dev/sdb2          121080      121602     4192257    5  Extended
/dev/sdb5          121080      121602     4192256   82  Linux swap / Solaris


sudo blkid

/dev/sda1: LABEL="Film" UUID="1E9EE0579EE0294B" TYPE="ntfs" 
/dev/sdc1: UUID="2A7AE7C37AE78A41" TYPE="ntfs" 
/dev/sdb1: LABEL="Main install" UUID="ea297717-6434-423c-9b06-ddd123dcc0ff" TYPE="ext4" 
/dev/sdb5: UUID="ce17ca3d-5f5a-4852-8ba4-dbeff5fbff20" TYPE="swap" 

cat /etc/fstab

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ce17ca3d-5f5a-4852-8ba4-dbeff5fbff20 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


cat /etc/mtab 

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ce17ca3d-5f5a-4852-8ba4-dbeff5fbff20 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


## Thank you for any help in making this transition to linux a smooth one! ##

---

### Post by Morbius1 on 2011-08-29
I'm very confused by the info you posted:
> [COLOR=Blue]/dev/sda1: LABEL="Film" UUID="1E9EE0579EE0294B" TYPE="ntfs" [/COLOR]
/dev/sdc1: UUID="2A7AE7C37AE78A41" TYPE="ntfs" 
/dev/sdb1: LABEL="Main install" UUID="ea297717-6434-423c-9b06-ddd123dcc0ff" TYPE="ext4" 
/dev/sdb5: UUID="ce17ca3d-5f5a-4852-8ba4-dbeff5fbff20" TYPE="swap" 
> [COLOR=Blue]/dev/sda1       /               ext4    errors=remount-ro 0       1[/COLOR]
UUID=ce17ca3d-5f5a-4852-8ba4-dbeff5fbff20 none            swap    sw              0       0I don't know how you are able to boot into this machine. Are you getting this info from a rescue disk?

I can understand why this is happening. Every now and then the system gets confused and can "flip" partitions unless they are expressed in UUID's and I don't think "Disk Utility" knows anything about UUID's.

Since Disk Utility touched this can you post the output of this command just in case:
```
sudo blkid -c /dev/null
```

---

### Post by JamboBuenna on 2011-08-29
Hey Morbius, 
Thank you for your quick response....this is on a running system not a recovery or similar.

After chucking the command 

sudo blkid -c /dev/null

into the terminal like you said I am getting the output

/dev/sda1: LABEL="Film" UUID="1E9EE0579EE0294B" TYPE="ntfs" 
/dev/sdc1: UUID="2A7AE7C37AE78A41" TYPE="ntfs" 
/dev/sdb1: LABEL="Main install" UUID="ea297717-6434-423c-9b06-ddd123dcc0ff" TYPE="ext4" 
/dev/sdb5: UUID="ce17ca3d-5f5a-4852-8ba4-dbeff5fbff20" TYPE="swap" 


Which I think means that the four attatched Hardrive partitions are the NTFS one with 2 and the linux one with ext 4 area and a swap area.

Hope this helps at all and thank again!
Sincerely
James

---

### Post by Morbius1 on 2011-08-29
> this is on a running system not a recovery or similar
Here's the problem with what your posted:

This line in your fstab:
> /dev/sda1 / ext4 errors=remount-ro 0 1Should make your system unbootable since /dev/sda1 points to an ntfs partition and that cannot be so.

That line should look like this:
```
UUID=ea297717-6434-423c-9b06-ddd123dcc0ff / ext4 errors=remount-ro 0 1
```Please post the output of this command since there's something I must be missing:
```
mount
```

---

### Post by JamboBuenna on 2011-08-30
Thank you for getting back to me so quickly, however am at work so will run that command once getting home tonight!
Thanks again!
James

Update ... 

After getting back I ran the command mount and it outputted

/dev/sdb1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/james/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=james)


I was wondering if you reakon I could solve this problem with a fresh install? My only thought is that I don't want to wipe either NFTS harddrive.

---

