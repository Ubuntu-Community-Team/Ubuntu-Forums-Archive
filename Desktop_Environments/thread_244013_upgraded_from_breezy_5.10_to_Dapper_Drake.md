---
title: "upgraded from breezy 5.10 to Dapper Drake"
date: 2006-08-25
forum: Desktop Environments
---

### Post by keheikev on 2006-08-25
I did the synaptic upgrade path to the new version everything has been working good for nearly two months yeaah!
However, Ive had trouble setting up my system to mount at boot up here its configured with two hdd on ide's 3 and 4 80 and 40 GB respectively. IDE 1 and 2 hold the two cd-rw and dvd-rw drives.
here is /etc/fstab file
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hde3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hde8       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0
/dev/hdh1     /media/windows vfat iocharset-utf8,umak-000  0    0
/dev/hdh2     /media/windows vfat iocharset-utf8,umask-000  0   0
/dev/hdh5     /media/windows vfat iocharset-utf8,umask-000  0   0
/dev/hdh6     /media/windows vfat iocharset-utf8,umask-000  0   0
/dev/hdh7     /media/windows vfat iocharset-utf8,umask-000  0   0
/dev/hdh8     /media/windows vfat iocharset-utf8,umask-000  0   0

It looks like the I set it to mount the 40 GB drives partitions for r/w but what did I do wrong?
Kiheikev :-\

kiheikev wrote:
> I had to install my fdd drive and now I cannot seem to mount one of my drives the 40 GB master on ide 4. It used to be the slave on  ide4 but I made it a master. So in total I have one dvd-r and cd-rw on IDE 1 and 2 and then the 80 GB on 3 and 40 on ide 4.
> here is sudo fdisk -l
>
> Disk /dev/hde: 80.0 GB, 80026361856 bytes
> 255 heads, 63 sectors/track, 9729 cylinders
> Units = cylinders of 16065 * 512 = 8225280 bytes
>
>    Device Boot      Start         End      Blocks   Id  System
> /dev/hde1   *           1         932     7486258+   7  HPFS/NTFS
> /dev/hde2            1735        9728    64211805    f  W95 Ext'd (LBA)
> /dev/hde3             933        1734     6442065   83  Linux
> /dev/hde5            1786        3355    12610993+   7  HPFS/NTFS
> /dev/hde6            3356        9728    51191091    7  HPFS/NTFS
> /dev/hde7            1775        1785       88326   82  Linux swap / Solaris
> /dev/hde8            1735        1773      313204+  82  Linux swap / Solaris
>
> Partition table entries are not in disk order
>
> Disk /dev/hdh: 40.0 GB, 40020664320 bytes
> 255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
>
>    Device Boot      Start         End      Blocks   Id  System
> /dev/hdh1   *           1        1020     8193118+   b  W95 FAT32
> /dev/hdh2            1021        4865    30884962+   f  W95 Ext'd (LBA)
> /dev/hdh5            1021        2040     8193118+   b  W95 FAT32
> /dev/hdh6            2041        2971     7478226    b  W95 FAT32
> /dev/hdh7            2972        3973     8048533+   b  W95 FAT32
> /dev/hdh8            3974        4865     7164958+   b  W95 FAT32
> here is mount
> kevin@kevinscomputer:~$ mount
> /dev/hde3 on / type ext3 (rw,errors=remount-ro)
> proc on /proc type proc (rw)
> /sys on /sys type sysfs (rw)
> varrun on /var/run type tmpfs (rw)
> varlock on /var/lock type tmpfs (rw)
> procbususb on /proc/bus/usb type usbfs (rw)
> udev on /dev type tmpfs (rw)
> devpts on /dev/pts type devpts (rw,gid=5,mode=620)
> devshm on /dev/shm type tmpfs (rw)
> lrm on /lib/modules/2.6.15-26-386/volatile type tmpfs (rw)
> /dev/hde1 on /tmp/disks-conf-hde1 type ntfs (rw)
> /dev/hde5 on /tmp/disks-conf-hde5 type ntfs (rw)
> /dev/hde6 on /tmp/disks-conf-hde6 type ntfs (rw)
> I dont think I want read write on ntfs crapola!
> I did use the following code so I would not have to remount drives every time I boot up. I want read access to the ntfs partitions and read/write to fat 32. btw what is the vfat for type?
>
> 
>
>
>         How to mount Windows partitions (FAT) on boot-up, and allow
>         all users to read/write
>
>     * Read #General Notes
>       <http://ubuntuguide.org/wiki/Dapper#General_Notes>
>     * Read #How to list partition tables
>       <http://ubuntuguide.org/wiki/Dapper#How_to_list_partition_tables>
>
>     /e.g. Assumed that /dev/hda1 is the location of Windows partition
>     (FAT)/     / Local mount folder: /media/windows/
> sudo mkdir /media/windows
> sudo cp /etc/fstab /etc/fstab_backup
> gksudo gedit /etc/fstab
>  
>     * Append the following line at the end of file
>
> /dev/hda1    /media/windows vfat  iocharset=utf8,umask=000  0    0
>  
well I did see that I put a dash instead of a equals sign so maybe thats why but I still cant browse the drives. I want my ntfs partitions for browsing and fat32 for r/w access. I would also like them to be shortcuts on my desktop like in Knoppix.
Kiheikev
Aloha!

---

### Post by Bachstelze on 2006-08-25
You're trying to mount six partitons on the same mountpoint, there's obviously a problem. You have to specify a different mountpoint for each of them, e.g. /media/hdh1, /media/hdh2 and so on. Don't forget to create the mountpoints with sudo mkdir.

---

### Post by keheikev on 2006-08-27
> **HymnToLife said:**
> You're trying to mount six partitons on the same mountpoint, there's obviously a problem. You have to specify a different mountpoint for each of them, e.g. /media/hdh1, /media/hdh2 and so on. Don't forget to create the mountpoints with sudo mkdir.
So each mountpoint needs a new directory. Is it more standard to have the hdd drives mounted in the /mnt directory versus the /media directory? My friends tell me /media is more for cdroms and removeable storage? Will the choice of mount point interfere with the graphical access to the drives thru system administration or the file browser?
When I make those directorys and then edited fstab that creates a mountpoint.
Kiheikev
Aloha!

---

### Post by keheikev on 2006-08-31
okay now I know what I wanted to do for this two hdd drive system in order to create read access at boot for the ntfs partitions and r,w access for the fat32 was create a separate mount point corresponding to each windows partition
Heres what I did I created 3 directorys in /mnt/windows_c windows_e, and windows_f for the three NTFS partitions and on other drive hdh1 I created five directories called /mnt/windows_J,k,L,m,n for the fat32 partitions.
Then I edited ```
 gksudo gedit /etc/fstab /deve/hde1 /mnt/windows_c ntfs nls=utf8,umask=0222 0    0 
```
heres my fstab file
fdisk -l

Disk /dev/hde: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *           1         932     7486258+   7  HPFS/NTFS
/dev/hde2            1735        9728    64211805    f  W95 Ext'd (LBA)
/dev/hde3             933        1734     6442065   83  Linux
/dev/hde5            1786        3355    12610993+   7  HPFS/NTFS
/dev/hde6            3356        9728    51191091    7  HPFS/NTFS
/dev/hde7            1775        1785       88326   82  Linux swap / Solaris
/dev/hde8            1735        1773      313204+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdh: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdh1   *           1        1020     8193118+   b  W95 FAT32
/dev/hdh2            1021        4865    30884962+   f  W95 Ext'd (LBA)
/dev/hdh5            1021        2040     8193118+   b  W95 FAT32
/dev/hdh6            2041        2971     7478226    b  W95 FAT32
/dev/hdh7            2972        3973     8048533+   b  W95 FAT32
/dev/hdh8            3974        4865     7164958+   b  W95 FAT32

BTW can someone please help me to make firestarter start at boot up without password I cant seem to edit my sudoers file or at least I can but the error message comes up that its a read only disk?
here is mount it still looks to be rw on the ntfs partitions?
 /dev/hde3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-26-386/volatile type tmpfs (rw)
/dev/hde1 on /mnt/windows_c type ntfs (rw,nls=utf8,umask=0222)
/dev/hde5 on /mnt/windows_e type ntfs (rw,nls=utf8,umask=0222)
/dev/hde6 on /mnt/windows_f type ntfs (rw,nls=utf8,umask=0222)
/dev/hdh1 on /mnt/windows_J type vfat (rw,iocharset=utf8,umask=000)
/dev/hdh5 on /mnt/windows_k type vfat (rw,iocharset=utf8,umask=000)
/dev/hdh6 on /mnt/windows_L type vfat (rw,iocharset=utf8,umask=000)
/dev/hdh7 on /mnt/windows_m type vfat (rw,iocharset=utf8,umask=000)
/dev/hdh8 on /mnt/windows_n type vfat (rw,iocharset=utf8,umask=000)
kev
Kiheikev
Aloha!

---

