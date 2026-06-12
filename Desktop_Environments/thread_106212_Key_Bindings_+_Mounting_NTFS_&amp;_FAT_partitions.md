---
title: "Key Bindings + Mounting NTFS &amp; FAT partitions"
date: 2005-12-20
forum: Desktop Environments
---

### Post by imranj on 2005-12-20
First issue is, i miss using short cuts due to windows habit, so i want some of them configured here too, i cannot find a place in KDE , where i can tell, globally to set these bindings. Any idea how?


Second is after i installed my own custom kernel, everything works fabluously, except for i cannot mount my NTFS & Fat32 parititions as it could be done in my earlier kernels the K7 one.

>>>Issue Output<<<<
ijamadar@shj-mjz-bsr2084:~$ sudo mount /dev/hda1 /media/ntfs
Password:
mount: /dev/hda1 already mounted or /media/ntfs busy
ijamadar@shj-mjz-bsr2084:~$


ijamadar@shj-mjz-bsr2084:~$ sudo mount -a
mount: /dev/hda1 already mounted or /media/ntfs busy
mount: /dev/hda3 already mounted or /media/fat busy

 /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
/dev/hdb1 / reiserfs notail,atime,auto,rw,dev,exec,suid,nouser 0 1
/dev/hdb5 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0 /media/floppy0 auto ,atime,noauto,rw,dev,exec,suid,user 0 0

/dev/hda1 /media/ntfs ntfs nls=utf8,umask=0222 0 0
/dev/hda3 /media/fat vfat iocharset=utf8,umask=000 0 0


>>>>More Info<<<<
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7139    57343986    7  HPFS/NTFS
/dev/hda2            7140        9728    20796142+   f  W95 Ext'd (LBA)
/dev/hda3            9729        9729        8032+   c  W95 FAT32 (LBA)
/dev/hda5            7140        9728    20796111    b  W95 FAT32

Disk /dev/hdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2273    18257841   83  Linux
/dev/hdb2            2274        2434     1293232+   5  Extended
/dev/hdb5            2274        2434     1293201   82  Linux swap / Solaris


Note: I have complied both, ntfs module and fat32 modules in the kernel.

Please advise.

---

### Post by imranj on 2005-12-20
Hello Can any one please help me. its being an hour? some body?

---

### Post by ad noiseam on 2005-12-20
[QUOTE=imranj]First issue is, i miss using short cuts due to windows habit, so i want some of them configured here too, i cannot find a place in KDE , where i can tell, globally to set these bindings. Any idea how?[/QUOTE]

Use [Xev](http://ubuntuforums.org/showthread.php?t=106209&highlight=xev) to see the keycodes for the key you are after, then map them with [Xbindkeys](http://ubuntuforums.org/showthread.php?t=104230), and finally make it [start at startup](http://ubuntuforums.org/showthread.php?t=100517).

Search the forums for more info on xev and xbindkeys, they are quite easy to use.

Good luck,

Nicolas

---

### Post by imranj on 2005-12-20
key bindings in KDE for KDE applications and use not generally.

---

### Post by ad noiseam on 2005-12-20
[QUOTE=imranj]key bindings in KDE for KDE applications and use not generally.[/QUOTE]

I am not sure I understand what you mean.

---

### Post by imranj on 2005-12-20
See in windows we use the winkey+ D to minimize the, windows which are active?

So how do i do the same in linux+KDE, got it?:D

---

### Post by imranj on 2005-12-20
ijamadar@shj-mjz-bsr2084:~$ mount /media/fat
mount: only root can mount /dev/hda3 on /media/fat
ijamadar@shj-mjz-bsr2084:~$ sudo mount /media/fat
mount: /dev/hda3 already mounted or /media/fat busy
ijamadar@shj-mjz-bsr2084:~$



ijamadar@shj-mjz-bsr2084:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb1              18G  3.3G   15G  19% /
tmpfs                 253M     0  253M   0% /dev/shm
ijamadar@shj-mjz-bsr2084:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
/dev/hdb1 / reiserfs notail,atime,auto,rw,dev,exec,suid,nouser 0 1
/dev/hdb5 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0 /media/floppy0 auto ,atime,noauto,rw,dev,exec,suid,user 0 0

/dev/hda1 /media/ntfs ntfs nls=utf8,umask=0222 0 0
/dev/hda3 /media/fat vfat iocharset=utf8,umask=000 0 0

---

