---
title: "[SOLVED] File permissions cannot be changed as root"
date: 2009-05-04
forum: General Help
---

### Post by UBUminJ on 2009-05-04
I have a directory copied from a USB-HDD (origin of the files is WinXP).
At the copied directory is the tag "readonly".

I tried to change the permissions that I can move the files (and directories) in it.

using gksudo nautilus, I moved to the directory and in the properties window, I tried to change the permission to create and delete files for owner/group/others from --- to read and write.
As soon as I click on "Apply permissions to Enclosed Files", it reverts back to the old state.
What to do next ?

Thanks
Michael

---

### Post by _Purple_ on 2009-05-04
What type of file is it?

---

### Post by UBUminJ on 2009-05-04
1) Folders
2) mp3

---

### Post by aysiu on 2009-05-04
If it's NTFS or FAT32, you change the permissions through different mount options in the /etc/fstab file. Those filesystems do not adhere to regular Unix-like permissions.

---

### Post by UBUminJ on 2009-05-04
first NTFS -> FAT32 (USB-HDD)
from there I copied it to my Ubuntu filesystem

If it has to do with the mount properties - why are there files which can be moved/deleted and others which cannot ?

So, how can I delete this directory ?

---

### Post by aysiu on 2009-05-04
So the files are now on Ext3? Maybe it's a bug in Nautilus or something.

What happens when you try to change permissions via [the terminal](http://www.psychocats.net/ubuntu/terminal)? ```
sudo chmod -R 755 /path/to/copied/directory
```

---

### Post by UBUminJ on 2009-05-04
Thank you very much.
That did it.
:-)

---

