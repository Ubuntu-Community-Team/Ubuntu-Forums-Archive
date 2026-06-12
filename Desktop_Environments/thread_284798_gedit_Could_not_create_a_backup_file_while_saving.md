---
title: "gedit: Could not create a backup file while saving"
date: 2006-10-26
forum: Desktop Environments
---

### Post by chinaski on 2006-10-26
hello,

after a reinstall of Dapper Drake it happens that sometimes when I try to save a document I just create with Gedit, this error appears (see attachment)

I must say that if I choose save anyway, everything goes fine, but still I need to understand what's this about

thanks in advance ;)

---

### Post by michux on 2006-10-26
> **chinaski said:**
> hello,

after a reinstall of Dapper Drake it happens that sometimes when I try to save a document I just create with Gedit, this error appears (see attachment)

I must say that if I choose save anyway, everything goes fine, but still I need to understand what's this about

thanks in advance ;)

It may be that you do not have proper permissions to the folder where you have the file you are editing. You may have a write permission to the exact file but not to the folder in general. Try invoking ```
ls -la
``` in this folder to check this.

---

### Post by chinaski on 2006-10-26
thank you very much for your reply michux

here's the output of the command you suggested, in that particular folder

```
drwxrwxrwx 10 root root 16384 2006-10-16 23:16
```that folder is in my second HD, a FAT32 partition, here's its entry in fstab

```
/dev/hda1    /mnt/disk2    vfat    iocharset=utf8,umask=000 0 0
```is there anything wrong?

---

### Post by johso on 2007-03-10
Should anyone else be looking for the cause of this error, I'm quite sure it's because you're trying to save on a FAT32 partition. I get the same error myself, but only when I try to save something on my FAT32 partition. My conclusion is that it has something with permissions to do, which FAT32 doesn't support at all.

No solution, I'm sorry, but I hope I could at least enlighten you :)

---

