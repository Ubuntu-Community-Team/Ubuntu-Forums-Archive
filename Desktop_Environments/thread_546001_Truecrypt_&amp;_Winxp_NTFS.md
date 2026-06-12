---
title: "Truecrypt &amp; Winxp NTFS"
date: 2007-09-08
forum: Desktop Environments
---

### Post by TheValk on 2007-09-08
have checked the forums but I can't find anything quite like the problem I have.
I have used Truecrypt on windows since it was first announced and it suits me fine.
I am dual booting WinXP and Ubuntu 7.04 and I thought it would be useful to share a Truecrypt folder between the two OS and have write access from both.
The folder is formatted NTFS, (I don't want to use FAT for a number of reasons), so I installed Truecrypt and ntfs-3g.
I can mount my folder using -
"sudo truecrypt --mount-options gid=100,uid=1000,umask=000 --filesystem ntfs-3g /media/Data/myfile /home/meuser/tc/"
I can read and use all the files in the folder.
I can create new folders and copy to and from the encrypted folder.
However, any changes I make do not survive a dismount and remount of the Truecrypt folder. It reverts to its original state!
I have loaded Forcefield 0.91 and the problem remains. I do get an error from Forcefield on mount. The error is
Couldn't find "/home/meuser/%d" but the file mounts OK.
Any help would be useful.

---

### Post by TheValk on 2007-09-08
I have, happily, fixed this.
Although I specified --file system ntfs-3g in my truecrypt command I had omitted to specify ntfs-3g in my fstab.
changed it from
UUID=9C3834063833DDC9 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
to
UUID=9C3834063833DDC9 /media/hda1     ntfs-3g   defaults                                              0       1
and all is well.

---

