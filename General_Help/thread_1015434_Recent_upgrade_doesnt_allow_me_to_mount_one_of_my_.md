---
title: "Recent upgrade doesnt allow me to mount one of my NTFS partitions."
date: 2008-12-18
forum: General Help
---

### Post by slicemaster on 2008-12-18
well, i always keep my Ubuntu up to date but recently i have been extremely frustrated with it because i believe an update broke my NTFS mounting ability of one of my partitions. so here is the situation, i have one hard drive with 3 partitions on it. i have linux on one partition formated in EXT3 or what ever the linux file system is, and i dual boot Windows xp pro x64 edition so windows in on another partition formatted in NTFS and then i have a data partition that i use as a common drive for data on both Ubuntu and windows. anyways, the data drive was set to mount automatically on startup but it stopped working just out of the blue. it also wont allow me to mount the partition from the "computer" window as it gives me this error...

unprivileged user can not mount ntfs block devices using external fuse library. either mount the volume as root, or rebuild ntfs-3g with integrated fuse support and make it setuid root. please see more information at...

i don't get it, it had no problems before and it still has no problems if i try to mount my ntfs partition that windows is installed on, it simply refuses to mount my data partition. what is causing this and how do i fix it?

---

### Post by taurus on 2008-12-18
Can you post the outputs of these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by slicemaster on 2008-12-19
```

rand@rand-desktop:~$ sudo fdisk -l
[sudo] password for rand: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2a4a2a49

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4844    38909398+   7  HPFS/NTFS
/dev/sda2            4845       23967   153605497+   7  HPFS/NTFS
/dev/sda3           23968       30046    48829567+  83  Linux
/dev/sda4           30047       30399     2835472+  82  Linux swap / Solaris
rand@rand-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=b89cc69e-530a-474e-9b60-d4cd74d67320 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=8221ce56-2e28-48c0-9bca-e97bc38a0b79 none            swap    sw              0       0
#CD-Rom Dirves
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
#NTFS Data Drives
/dev/sda2	/media/DATA	ntfs	auto,user,exec,rw	0	0
rand@rand-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              47G   32G   13G  73% /
varrun                503M  220K  503M   1% /var/run
varlock               503M     0  503M   0% /var/lock
udev                  503M   72K  503M   1% /dev
devshm                503M   52K  503M   1% /dev/shm
lrm                   503M   44M  459M   9% /lib/modules/2.6.24-21-generic/volatile
gvfs-fuse-daemon       47G   32G   13G  73% /home/rand/.gvfs

```

ok there is the text output from running each of those commands.... but i am not sure if it will help....it used to work with this exact configuration and now it just stopped and started throughing me that stupid error that means absolutely nothing to a normal person.

thanks

---

### Post by dcstar on 2008-12-19
> **slicemaster said:**
> 
........
i don't get it, it had no problems before and it still has no problems if i try to mount my ntfs partition that windows is installed on, it simply refuses to mount my data partition. what is causing this and how do i fix it?

If the partition is marked as corrupted - or suspect - then it cannot be mounted.

Install the **ntfsprogs** package and then run **ntfsfix** on the partition.

---

### Post by slicemaster on 2008-12-19
> **dcstar said:**
> If the partition is marked as corrupted - or suspect - then it cannot be mounted.

Install the **ntfsprogs** package and then run **ntfsfix** on the partition.
why would it be detected as corrupt? how do you know Ubuntu is detecting it as corrupt? i ran a check disk in windows and it detected no issues.

---

### Post by blazemore on 2008-12-19
can you force it with

```
mount /dev/sd**XX** /-t ntfs /**mountpoint** -O force
```

That's O for Orange

---

### Post by slicemaster on 2008-12-19
none of the solutions that have been recommended explain why Ubuntu broke it in the first place. i understand that many of the recommendations are good workarounds but that doesn't change the fact that their is an underlaying problem with Ubuntu and or the software it uses to use NTFS drives.

note: i know i can mount the drive manually from terminal by executing the command: sudo mount /dev/sda2 /media/temp  this mounts that partition and allows me to be able to read and write to the drive with no problems...the problem is that the drive will not auto mount as dictated in the fstab and that it gives me that bulls$it error when i try to mount it from Nautilus using the simple double click method. it does this whether or not i try to the double click method as root or as a regular user....note that the other NTFS partition has no problems mounting using the double click method in Nautilus as a user or as root....bottom line i can only get that partition to mount using terminal.

---

### Post by blazemore on 2008-12-19
Well you have to remember that Ubuntu uses a standard ntfs implementation, the same as all distros.
NTFS support is never going to be perfect, since Microsoft choose not to release the code for it. All the implementations are simply very good guesses.

Therefore it's not advisable for using ntfs for important data in Linux. If you want to share data between Linux and Windows, a FAT32 drive is far better supported, since both can read it natively.

---

### Post by slicemaster on 2008-12-19
> **blazemore said:**
> Well you have to remember that Ubuntu uses a standard ntfs implementation, the same as all distros.
NTFS support is never going to be perfect, since Microsoft choose not to release the code for it. All the implementations are simply very good guesses.

Therefore it's not advisable for using ntfs for important data in Linux. If you want to share data between Linux and Windows, a FAT32 drive is far better supported, since both can read it natively.

as i described above it is not a problem reading or writing to the drives...as a matter of fact Ubuntu does a great job with that. i am simply pointing out what i believe to be a software bug, as i have found no other explanation for this odd behavior. i am posting this in hopes that someone will fix it, the fact that the partition mounts perfectly using terminal commands is proof that the NTFS implementation is working properly. it is simply disturbing that a bug like this got through quality control. the fstab, a very basic system config file, doesn't function properly, and Nautilus cant mount the drive either using the traditional double click method either. i find it interesting and hope that it will stimulate a bug fix. termanal commands work, fstab and Nautilus don't. i am looking for the answer as to WHY fstab and nautilus aren't working properly with this one partition but they work fine with the other ntfs partition, it doesn't make any sense. has to be a bug.

---

### Post by vanadium on 2008-12-19
Instead of speculating, we'd beter try to find out what is going wrong with the mounting or with fstab. Anyway, before attempting anything else, you should have the drive checked and eventually repaired using MS Windows. Chances are high that that alone will solve the issue.

If that does not solve the issue, execute the following command and post the output here (if any): if there is an error, it will be displayed in the console.

```

sudo mount -a

```

I have some remarks on previous replies:

[quote=blazemore]Therefore it's not advisable for using ntfs for important data in Linux.[/quote]
I do not agree. You can perfectly use an ntfs volume under Linux for reading and writing. The problem, though, is that the capabilities of linux to check and repair an ntfs volume are limited. Therefore, one should only use ntfs partitions if the drive can be checked using MS Windows (whihc is the case for the OP).

[quote=dcstar]Install the ntfsprogs package and then run ntfsfix on the partition. [/quote]

is, for the reason stated above, not the best advice. You should first of all check and repair an ntfs volume using MS Windows. Nevertheless, ntfsfix can fix simple problems and can be useful in non-critical cases (you have a backup elsewhere) and when MS Windows is not available.

You should also normally not force mount, unless you have no alternative to rescue the data. If linux refuses to mount an ntfs by default, it is because mounting can cause further corruption of the ntfs volume.

My general advice:

(1) Only maintain ntfs volumes if you can access the drive with MS Windows. Otherwise, convert to ext3 or another native linux format, or fat32 if compatibility is required and fat limits are not an issue.

(2) If you have any problem with an ntfs volume under Linux, first of all have it checked and repaired using MS Windows. Shut down Windows completely when done, or, for removable drives, disconnect the drive using the "Safely disconnect hardware" in Windows. A "healthy" ntfs volume is mounted and used without problems with linux.

---

### Post by PierreDeKat on 2008-12-19
I have had Ubuntu refuse to mount an NTFS partition if Windows had a bad shutdown -- like it crashed, and I didn't bother to reboot and shut down normally. Of course, it tells me that, IIRC, in a "Details" grippy thing.

But your details say something to the effect of: *"unprivileged user can not mount ntfs block devices using external fuse library. either mount the volume as root, or rebuild ntfs-3g with integrated fuse support and make it setuid root. please see more information at..."*

Seems to me that there's a read/write privilege issue there.

Anywho, FWIW, I had trouble with trying to set up read/write privileges on an NTFS drive for my daughter without actually giving her Administrative privileges, and I ended up using NTFS-config out of the repositories to do it.

Previously, I had edited fstab myself on other computers, but I couldn't seem to get fstab to do what I wanted on that particular computer, and NTFS-config did exactly what I needed in a real easy way.

One other thing to look at would be the possibility that your mount point, UUID, or whatever got changed by some other change you did, and now fstab is confused.

A confused fstab will prevent you from mounting the drive, too.

I don't know, just some random thoughts. Maybe something there is useful.

---

