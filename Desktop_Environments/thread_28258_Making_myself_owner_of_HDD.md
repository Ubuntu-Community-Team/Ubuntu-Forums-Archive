---
title: "Making myself owner of HDD?"
date: 2005-04-19
forum: Desktop Environments
---

### Post by coldturkey on 2005-04-19
My 200GB Harddrive, NTFS, that i mounted is "not mine". I don't have any rights to change anything. How can I fix this problem? Is there a way to remove all these folders that are not ment to be there (eg. RECY. temp)?
I really don't wanna format it, i have some really important files on it.
If formating is the only way out, could you please tell me howto??

Thanks in advance :)

---

### Post by nad on 2005-04-19
NTFS filesystems are necessarily mounted read only. All you can do is view and copy files from it.

Edit: Perhaps you wish to create another partition with an ext2/3, ReiserFS, XFS, vfat ... filesystem and copy everything over.

Dan M

---

### Post by mike998 on 2005-04-19
If you pull the files you want off the drive, you can the format / repartition with gparted (I think that's the name) - I used that package this weekend with a USB hard drive and it was a resounding success.

---

