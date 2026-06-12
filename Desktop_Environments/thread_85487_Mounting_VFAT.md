---
title: "Mounting VFAT"
date: 2005-11-02
forum: Desktop Environments
---

### Post by NXArmada on 2005-11-02
I have followed all the instruction to mount a VFAT partition read/write and i have it setup in FSTAB but evertime i do sudo mount -a or reboot it does mount the drive but i can not write to it.

Here is what my FSTAB looks like:
```

proc            /proc           proc    defaults        0       0
/dev/hdc1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc5       none            swap    sw              0       0
[COLOR="blue"]/dev/hdd1       /media/drive-d  vfat    iocharset=utf8,umask=000   0       0[/COLOR]
/dev/hda        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0

```

The blue line is the drive.

i can read the drive fun but i can't write.

---

### Post by RAOF on 2005-11-02
You could have a look at this [wiki page]("https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions?highlight=%28windows%29").

Or, I think just adding an extra '0' to umask=000, making it umask=0000, will do it.  Possibly.

---

### Post by majikstreet on 2005-11-02
[QUOTE=RAOF]You could have a look at this [wiki page]("https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions?highlight=%28windows%29").

Or, I think just adding an extra '0' to umask=000, making it umask=0000, will do it.  Possibly.[/QUOTE]
According to that article, that will do it.

I would personally get rid of the umask and put in "iocharset=utf8,rw,users".. I dunno if that will really work.

---

### Post by NXArmada on 2005-11-02
Thats a no go still says Read Only

---

### Post by Diod on 2005-11-02
umask=000 works perfectly on my side. i dont use iocharset=utf8, though

try deleting iocharset=utf8,

---

### Post by NXArmada on 2005-11-02
I did sudo fdisk -l and this is what came up

```

Disk /dev/hdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       14405   115708131   83  Linux
/dev/hdc2           14406       14593     1510110    5  Extended
/dev/hdc5           14406       14593     1510078+  82  Linux swap / Solaris

Disk /dev/hdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1       30401   244196001    7  [COLOR="Blue"]HPFS/NTFS[/COLOR]


```

Its show that my hdd1 partition is HPFS/NTFS and GParted and Disks in ubuntu show it as VFAT.  Whats up with this.   In any normal circumstance i would format hdd1 but i need the files on there.  Im trying to move files off of my Primary linux partition to hdd1 so i can re-install a fresh install of Ubuntu.

---

### Post by NXArmada on 2005-11-02
[QUOTE=Diod]umask=000 works perfectly on my side. i dont use iocharset=utf8, though

try deleting iocharset=utf8,[/QUOTE]


still coming up as read only.  :(

---

### Post by RAOF on 2005-11-02
Are you sure that's a fat32 drive?  I'd trust fdisk -l over the other tools - they may be reading your fstab.  If it **is** a NTFS partition, 'aint no way you'll be writing to it anytime soon.  You could look into the capive ntfs driver (ask dr google), but I've never tried to use it, nor have I seen any threads here about it.

---

### Post by NXArmada on 2005-11-02
I have written to the drive before when i formatted it to fat32 and about a week later i wasn't able to write to anymore.

---

### Post by dcstar on 2005-11-02
[QUOTE=NXArmada]I have written to the drive before when i formatted it to fat32 and about a week later i wasn't able to write to anymore.[/QUOTE]

Double-check that your /media/drive-d mount point has appropriate write permissions.

---

### Post by NXArmada on 2005-11-02
ls -l shows this

```
drwxrwxrwx  2 ryan ryan 4096 2005-11-02 18:22 drive-d
```

looks like its 777 to me the way i set it.

---

### Post by SickTwist on 2005-11-02
The thing is that fat32 does not have a way to store permissions on files. But since Linux does use permissions, it will use a default set of permissions (that can be set to whatever you want) while the filesystem is mounted. This can be set up a few ways depending on how you want to use this partition:

-read/write for any user
-read/write for only yourself with read access for otherscat /etc/passwd | grep `whoami`

-read/write for only yourself with no read access for others
etc.

If you want read/write access for only yourself, try this:

**/dev/hdd1 /media/drive-d vfat defaults,uid=[COLOR="Blue"]X[/COLOR],gid=[COLOR="Green"]Y[/COLOR],umask=077,utf8 0 0**

[COLOR="Blue"]X[/COLOR] must be replaced with your user ID number (this will make all files owned by you) and [COLOR="Green"]Y[/COLOR] must be replaced with your group ID number (which will make all files part of your group). Keep in mind that these permissions aren't permanent, they're just used to tell Linux how to grant access sine fat32 cannot do it. To find out what your user and group numbers are run this command (just copy and paste it in a terminal):

**cat /etc/passwd | grep `whoami`**

You'll see a string of stuff seperated by colons. The first number in this line (third column) is your user ID (uid), the second number (fourth column) is your group ID (gid).

The umask part hides the files from everyone but you. If you want to set it up differently just explain what you want to do and we'll help you figure it out. Also, remember not to include any spaces between the mount options ( defaults,uid=X,gid=Y,umask=077,utf8 ) because whitespace is used to parse the columns.

---

