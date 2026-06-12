---
title: "NTFS acts strange"
date: 2005-10-21
forum: Desktop Environments
---

### Post by kurtkraut on 2005-10-21
I have to hard disks, one dedicated to Ubuntu and the other one to Windows. I'm attemping to migrate all important data from Windows-HD to Ubuntu-HD and them install the Windows-HD in a older machine.

I can mount this NTFS HD following the instructions inhttp://www.ubuntuguide.org/#mountunmountntfs but something stranges happen: I can list all files in the HD, nautilus and the ls command shows them perfectly. But I cannot open the files neither copy them to Ubuntu-HD.

This HD, while accessed thru Windows, presents no problem. How could I solve this ? I can't lose this Windows-HD data.

---

### Post by invalid on 2005-10-21
I can't right off hand tell you the exact method to do this..
But I can tell you that the method in the UbuntuGuide is for "Read Only" .. so that would explain your problems

Cb

---

### Post by fimbulvetr on 2005-10-21
Are you sure you mounted it with this command:
```

sudo mount /dev/hda1 /media/windows/ -t vfat -o iocharset=utf8,umask=000

```

??

If you forgot the umask=000, you won't have the correct permissions.

If that's not the issue, paste the output of the "dmesg" command when run from the command line.

---

### Post by invalid on 2005-10-21
[QUOTE=fimbulvetr]Are you sure you mounted it with this command:
```

sudo mount /dev/hda1 /media/windows/ -t vfat -o iocharset=utf8,umask=000

```

??

If you forgot the umask=000, you won't have the correct permissions.

If that's not the issue, paste the output of the "dmesg" command when run from the command line.[/QUOTE]

Note that this is for FAT file format.. not NTFS

Cb

---

### Post by kurtkraut on 2005-10-21
[QUOTE=invalid]I can't right off hand tell you the exact method to do this..
But I can tell you that the method in the UbuntuGuide is for "Read Only" .. so that would explain your problems

Cb[/QUOTE]


I know that NTFS is only readable. I'm not trying to write on NFTS. I'm just trying to copy files from NTFS to EXT3 or just read files (e.g. a .txt) thru Ubuntu and I just can't do that.

---

### Post by heart_reaver on 2005-10-21
This may be because you are logged as normal user not not as supper user to get access for your folder, that you have mounted as super user thus you are able to see the list in terminal but not in file browser. 

For solving this thread you again go to [http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)


 look for fstab edit section to permanetly mount your fat or ntfs file system. This also helps in making your partions get mounted at the time of booting with read/write mode even as general user mode

---

### Post by kurtkraut on 2005-10-21
[QUOTE=heart_reaver]This may be because you are logged as normal user not not as supper user to get access for your folder, that you have mounted as super user thus you are able to see the list in terminal but not in file browser. 

For solving this thread you again go to [http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)


 look for fstab edit section to permanetly mount your fat or ntfs file system. This also helps in making your partions get mounted at the time of booting with read/write mode even as general user mode[/QUOTE]


I've done all ubuntuguide.org procedures, including fstab. I've got the same error for all. Any hints ?

---

