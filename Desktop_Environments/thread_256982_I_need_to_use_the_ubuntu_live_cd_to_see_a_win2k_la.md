---
title: "I need to use the ubuntu live cd to see a win2k laptop drive"
date: 2006-09-13
forum: Desktop Environments
---

### Post by Justin Holt on 2006-09-13
Hi all, i just got this laptop from my robotics team leader, and it has win2k as the title stated, i need to know what i would do to look at the drive through a ubuntu live cd because it has a password no one knows, or if you know what i could use to crack the password...that would help too, any response welcome :-D

---

### Post by Justin Holt on 2006-09-13
i guess im asking...how do i mount the drive to look and see the files and possibly back them up to my flash drive

---

### Post by aysiu on 2006-09-14
Ideally, you'd use a Knoppix CD--since those are *designed* for recovery purposes. Ubuntu CDs aren't designed for recovery, but they can be *used* for recovery.

Open a terminal.

Type ```
sudo fdisk -l
``` Note the name of the Windows partition and the filesystem. For the first example, let's say it's /dev/hda1 and NTFS. ```
sudo mkdir /media/recovery
sudo mount -t ntfs /dev/hda1 /media/recovery -o nls=utf8,umask=0222
``` For the second example, let's say it's /dev/hda2 and FAT32. ```
sudo mkdir /media/recovery
sudo mount -t vfat /dev/hda2 /media/recovery -o iocharset=utf8,umask=000
```

---

### Post by p388l3s on 2006-09-14
Why not just look up resetting the password for windows 2000 thru google or ms technet? i ask only because this is pretty well covered by MS, if you mount the drive thru linux you'll still run into permission issues and unless you have ntfs write support in the distro you use you'll not be able to reset the permissions for both files and directories, trust me this can get very messy very quickly ( i've played around with this type of scenario ), if it's formatted to fat32 then things get a little easier but still troublesome.

just to help: give this link a shot.

[http://home.eunet.no/~pnordahl/ntpasswd/](http://home.eunet.no/~pnordahl/ntpasswd/)

hope that helps.

Pebbles

---

