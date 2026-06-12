---
title: "chown problems"
date: 2009-05-20
forum: General Help
---

### Post by Josh61980 on 2009-05-20
hi all I'm running the following command 
sudo chown jcrocker\: iPhone/

and getting the following error
chown: changing ownership of `iPhone/': Function not implemented


root currently owns the directory.  Any help would be appreciated, thank you.

---

### Post by Josh61980 on 2009-05-20
I'm also getting it on chmod
command:
sudo chmod 644 /media/iPhone/

output:
chmod: changing permissions of `/media/iPhone/': Function not implemented

---

### Post by geraldvillorente on 2009-05-20
```

sudo chown -R jcrocker <dir_to_be_chowned>

```
and then
```

sudo chmod 644 -R /media/iPhone - use -R to apply chmod recursively

```

---

### Post by Josh61980 on 2009-05-20
Same issue

```
sudo chown jcrocker /media/iPhone/
```

output:
chown: changing ownership of `/media/iPhone/': Function not implemented

if I include the -R flag it gives the same error on all the subdirectories and files.

---

### Post by drs305 on 2009-05-20
You are probably trying to change the ownership of a non-linux file system. Chown will work on ext2/3/4 formats but if you are trying to do this on fat16/32 or ntfs it will give you the message you are getting.

Ownership is set at the time of mounting and can't be changed once mounted. What you are describing is normal for an ntfs partition: owned by root (but you should still have read/write access).

---

### Post by pereclies on 2011-02-03
> Ownership is set at the time of mounting and can't be changed once mounted. What you are describing is normal for an ntfs partition: owned by root (but you should still have read/write access).

How would one change permissions then? I've got this problem with an exfat file system. It's gonna be a real pain to have to move +1.5TB of info just to reformat into ext*

---

### Post by mcduck on 2011-02-03
> **pereclies said:**
> How would one change permissions then? I've got this problem with an exfat file system. It's gonna be a real pain to have to move +1.5TB of info just to reformat into ext*

The permissions for non-linux filesystems are defined for the whole partition at the time it's mounted, and you can change them by configuring the drive in /etc/fstab.

---

### Post by drs305 on 2011-02-03
Here is a nice guide on fstab and explains permissions as well:
[http://ubuntuforums.org/showthread.php?&t=283131]("http://ubuntuforums.org/showthread.php?&t=283131")

---

