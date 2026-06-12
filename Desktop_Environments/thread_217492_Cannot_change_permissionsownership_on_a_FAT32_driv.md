---
title: "Cannot change permissions/ownership on a FAT32 drive"
date: 2006-07-17
forum: Desktop Environments
---

### Post by rudlavibizon on 2006-07-17
I have a FAT32 partition which i use as share drive with WinXP and i'd like to change  read/write/execute permissions for others in a folder for nicotine. I tried browsing as root then in the properties simply checking the boxes but it doesn't work. I tried changing the owner and group and i get the message: "The owner could not be changed.Sorry, couldn't change the owner of "nicotine"" . I also tried the same from the console but to no avail. I wanted to change this because nicotine couldn't write the files i download. This, however, happened only recently, i didn't have any trouble with nicotine before.:confused:  Please help.

ps: file owner (of that folder) : root
    file group : plugdev

---

### Post by mogelhead on 2006-07-17
Windows partitions does not support linux file permissions.

When you mount your windows partition it is possible to set the permissions for the whole drive.

---

### Post by geco on 2006-07-17
> **rudlavibizon said:**
> I have a FAT32 partition which i use as share drive with WinXP and i'd like to change  read/write/execute permissions for others in a folder for nicotine. I tried browsing as root then in the properties simply checking the boxes but it doesn't work. I tried changing the owner and group and i get the message: "The owner could not be changed.Sorry, couldn't change the owner of "nicotine"" . I also tried the same from the console but to no avail. I wanted to change this because nicotine couldn't write the files i download. This, however, happened only recently, i didn't have any trouble with nicotine before.:confused:  Please help.

ps: file owner (of that folder) : root
    file group : plugdev

edit your /etc/fstab file to set the permissions,

try something like this:
```

#DEVICE          MOUNT POINT    FILE SYSTEM          PERMISSIONS
/dev/hda2       /mnt/winc       vfat       rw,exec,uid=1000,gid=1000,auto  0      0

```

"uid" and "gid" tags tell to Linux which owner (user and group) to set, you must change them to user and owner id that you prefer, to discover gid and your uid of any user do this:
```

id user_name

```

if you omit "user_name" your uid and gid will be returned, surely you will have many gid, don't worry about this!

"auto" option means that the filesystem is mounted on boot.

you can learn more typing
```

man fstab

```

```

man mount

```

```

man id

```

byebye.

---

### Post by rudlavibizon on 2006-07-17
Thanks for the quick reply. I changed fstab line from:
/dev/sdb6       /media/sdb6     vfat    defaults,utf8,umask=007,gid=46 0     1
to:
/dev/sdb6       /media/sdb6     vfat    defaults,utf8,umask=0000,uid=1000,gid=1000 0       1

and.......IT WORKED!

---

### Post by bung33 on 2007-05-21
I'm having a similar problem. I have an external hard drive that I am trying to gain ownership of. I have tried modifying the users and groups, but that won't work. I've tried the solution above, but can't seem to figure it out. The output of mount is as follows...

```

/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdb1 on /media/LACIE type ntfs (rw,nosuid,nodev,umask=222,utf8)

```

The external hard drive is at the bottom of the list. My fstab file looks like...

```

proc /proc proc defaults 0 0
UUID=280017cf-1bbd-4eb9-81f5-31c03d2b5c7d / ext3 defaults,errors=remount-ro 0 1
UUID=20c14150-41b2-4c63-9395-6243a6bd7f6b none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0

```

I'm not quite sure what I should edit in the fstab file. Should my drive be listed so that I can edit the entry, or do I need to create a new entry?

---

### Post by bung33 on 2007-05-28
OK... So I lack intelligence. My external hard drive was formatted NTFS. I thought Linux would have the capability of writing to that filesystem, but I guess I was wrong. After reformatting to EXT3, everything works as expected...

---

### Post by vibe666 on 2008-01-21
FYI, this won't help you share out fat32 disks, but the debian package of "disk manager" is very handy for auto-configuring RW access for fat32 or ntfs USB (or internal) drives in Ubuntu.

[http://flomertens.free.fr/disk-manager/index.html](http://flomertens.free.fr/disk-manager/index.html)

especially if (like me) you go all fuzzy headed every time someone mentions manually reconfiguring a config file. :)

---

### Post by gangrelsurf on 2008-01-21
Another option to this sharing drives between windoze and *nix thing is to make windows read/write ext* drives:
[http://www.fs-driver.org/](http://www.fs-driver.org/)
Saying you want a shared drive which is not also your windows system drive, of course

---

### Post by vibe666 on 2008-01-21
incidentally, I still am not able to share out my fat32 formatted disk using SMB.  does anyone know of an easy way to do this?  I can create a share, but it is not accessible over the LAN.

I've tried looking in users & groups for a group called plugdev, but I can't find one.  i have other similar ones like netdev and powerdev but no plugdev.

any ideas?

BTW, reformatting to ext3 is not an option for me as this drive wil be moved around quite a bit and used by non-technical windows users on various different machines.

---

### Post by jimbo99 on 2008-01-21
Please do not direct people to man pages.  Man pages are outdated and old fashion. Man pages need to be removed.  They also infer that the user must use a command line prompt.  This is also faulty logic.  All man pages should have been converted to the GUI help system long ago with hyper links included therein to allow easy navigation and searching.

Man pages are and should be dead.  Please stop directing people to man pages.

This is linux for the human being.  We are not trying to turn human beings into geeks here.  Try to understand that.

---

### Post by vibe666 on 2008-01-21
er, sorry but what's a man page?

and who were you talking to, me or the other guy?

BTW, I'm all for GUI's, but until all the things most people are likely to want to be able to do in Ubuntu are doable without dropping to the command line that's just not going to happen is it?

P.S.  I'm still looking for someone who can tell me how to share out my fat32 USB disk using an SMB share (via the GUI).  failing that, via the command line would do in a pinch, but editing conf files really ought not to be necessary.:)

---

### Post by vibe666 on 2008-01-26
can nobody answer my question?

EDIT:  well, I'm almost there.  I've got it down to either being able to share it but having it mounted read only or getting RW access, but not being able to access it over the network.

seemingly it's the difference between "umask=002" and "umask=077" but I have no idea what these parameters do.

help me ubuntuwan kenobi, you're my only hope....

---

