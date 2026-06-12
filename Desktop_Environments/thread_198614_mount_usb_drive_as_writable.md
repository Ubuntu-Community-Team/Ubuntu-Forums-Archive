---
title: "mount usb drive as writable?"
date: 2006-06-17
forum: Desktop Environments
---

### Post by kabanta on 2006-06-17
I have an external USB hard-drive that I use for backups and large
files. It is having some troubles -- I can see and read most of the
data on it, but suddenly cannot write to it. And because of this, I
can't remove some corrupted files I just discovered on it.

The reading from "mount" is:

```
/dev/sda1 on /media/BACKUP-DRIVE type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)

```
I've tried unmounting the drive and then mounting it by hand, but
haven't succeeded to find the right combination of flags so I can
write to it.

Two questions:

[LIST]
[*]Where does ubuntu look to know how/where to mount a hot-plugged usb
  drive? (by analogy to /etc/fstab that tells it which local disks to
  mount, and where)
[*]Can someone suggest a way to get it to mount as writeable? I tried
  things like:

  ```
sudo mount -t vfat -o rw,user /dev/sda1 /media/BACKUP-DRIVE
```

But I still got the same error ("disk is not writable")
[/LIST]

thanks.

---

### Post by aysiu on 2006-06-17
Have you tried this? ```
sudo umount /dev/sda1
sudo mount -t vfat /dev/sda1 /media/BACKUP-DRIVE -o iocharset=utf8,umask=000
```

---

### Post by kabanta on 2006-06-17
[QUOTE=aysiu]Have you tried this? ```
sudo umount /dev/sda1
sudo mount -t vfat /dev/sda1 /media/BACKUP-DRIVE -o iocharset=utf8,umask=000
```[/QUOTE]

Thanks for the tip. After trying it, the drive *looks* writable:

```
ls -l BACKUP-DRIVE
total 1056
drwxrwxrwx  7 root root  32768 2006-06-17 10:16 DIR1
drwxrwxrwx  3 root root 688128 2006-02-04 13:08 DIR2
etc.
```
But if I try to delete or modify existing files (or create new ones), I still get errors stating that the drive is read-only. ?!?!

Note that this may be related to the reason I need to delete a directory on the drive. It is corrupted and this seems to be related to some encoding problems. (It's an old directory that I haven't looked at in a while. But when I went to resize the partition today, I ran into trouble and finally narrowed it down to this corrupted directory.) Anyway, I get "input/output errors" when I try to do anything with files in the directory. That's why I thought perhaps being able to rename the files would help. Which, in turn, led me to this read-only problem with the drive.

Unfortunately, there is so much else on that partition of the drive that I cannot easily move it and reformat the partition. So, any suggestions would e great.

---

### Post by steveneddy on 2006-06-18
[QUOTE=kabanta]Thanks for the tip. After trying it, the drive *looks* writable:

```
ls -l BACKUP-DRIVE
total 1056
drwxrwxrwx  7 root root  32768 2006-06-17 10:16 DIR1
drwxrwxrwx  3 root root 688128 2006-02-04 13:08 DIR2
etc.
```
But if I try to delete or modify existing files (or create new ones), I still get errors stating that the drive is read-only. ?!?!

Note that this may be related to the reason I need to delete a directory on the drive. It is corrupted and this seems to be related to some encoding problems. (It's an old directory that I haven't looked at in a while. But when I went to resize the partition today, I ran into trouble and finally narrowed it down to this corrupted directory.) Anyway, I get "input/output errors" when I try to do anything with files in the directory. That's why I thought perhaps being able to rename the files would help. Which, in turn, led me to this read-only problem with the drive.

Unfortunately, there is so much else on that partition of the drive that I cannot easily move it and reformat the partition. So, any suggestions would e great.[/QUOTE]


Try opening the folder from the USB stick in sudo nautilus and you will have root permissions and you can delete and modify anything there.

It worked for me, anyway.

---

### Post by kabanta on 2006-06-18
[QUOTE=steveneddy]Try opening the folder from the USB stick in sudo nautilus and you will have root permissions and you can delete and modify anything there.[/QUOTE]

Nice idea, but doesn't work here.

If I add columns in nautilus for seeing permissions, it shows the files with a strange mix of "unknown" owners and even "unknown" permissions. If I try to delete one that shows me as owner (and write permissions) I get the same error  as before: "cannot be deleted because it is a read-only disk."

I'm pretty sure this is something to do with the garbled file names in that directory. My guess: the OS is having trouble dealing with them as files, it makes dificult to determine file and directory boundaries on the file-system as a whole, so some kind of "protection" kicks in to prevent writing to and deleting from the disk. (I've even tried a few different types of terminal to see if perhaps better support for different encodings might help.)

---

