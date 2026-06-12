---
title: "Can`t remove this file"
date: 2009-03-09
forum: General Help
---

### Post by nothingspecial on 2009-03-09
I have this file on a usb stick -

```
-r--r--r-- 1 root root 13312 2009-03-09 09:12 extlinux.sys
```

I can not get rid of it, even gparted won`t let me reformat.

What do I do?

Thanks

---

### Post by stumbleUpon on 2009-03-09
The file is owned by root and does not have write permissions

If you are absolutely sure you want to delete it, then in a terminal go the usb stick folder and delete the file using sudo rm -f fileName

---

### Post by heindsight on 2009-03-09
> **stumbleUpon said:**
> The file is owned by root and does not have write permissions

If you are absolutely sure you want to delete it, then in a terminal go the usb stick folder and delete the file using sudo rm -f fileName

The ability to delete a file depends on the permissions you have in the directory containing the file, not the permissions for the file itself.

Do 
```
ls -ld /path
```
replacing /path with the actual path to the directory containing the file you want to delete.

Another possibility is that you have mounted your usb stick read-only, have a look at the output of:
```
mount
```
to see what mount options are in effect.

Also, I'm fairly sure that gparted won't reformat a mounted file system. Try unmounting first.

---

### Post by nothingspecial on 2009-03-09
> **stumbleUpon said:**
> The file is owned by root and does not have write permissions

If you are absolutely sure you want to delete it, then in a terminal go the usb stick folder and delete the file using sudo rm -f fileName

Thank`s for your reply but I already tried that

```
sudo rm -f extlinux.sys 
rm: cannot remove `extlinux.sys': Operation not permitted

```

I can`t chown or chmod it as root or like I said even reformat the drive.

It seems that root owns the file but even the all powerful root has only read permissions.

---

### Post by nothingspecial on 2009-03-09
> **heindsight said:**
> The ability to delete a file depends on the permissions you have in the directory containing the file, not the permissions for the file itself.

Do 
```
ls -ld /path
```
replacing /path with the actual path to the directory containing the file you want to delete.

Another possibility is that you have mounted your usb stick read-only, have a look at the output of:
```
mount
```
to see what mount options are in effect.

Also, I'm fairly sure that gparted won't reformat a mounted file system. Try unmounting first.

The drive is mounted and I can write to it. I did unmount the drive before trying to format it but I got an error.

I`m a bit stuck to be honest.

---

### Post by heindsight on 2009-03-09
What filesystem do you have on the USB stick?

If it's ext2, it may be that you have the immutable flag set on the file, or the directory containing it.

try using
```
lsattr extlinux.sys
lsattr -d /path
```
where path is again the path to the directory containing extlinux.sys
If either of those outputs something like:
```
----i------------- extlinux.sys
```
then you have an immutable flag set, which you can remove using (eg)
```
sudo chattr -i extlinux.sys
```

This would not explain why gparted won't reformat it though (the presence of immutable files shouldn't stop you from reformatting). Perhaps a bit more information could help. Can you post the output of
```
mount
```
and
```
sudo fdisk -l
```
with your usb stick mounted?

Also, exactly what is the error you get from gparted?

---

### Post by nothingspecial on 2009-03-09
> **heindsight said:**
> What filesystem do you have on the USB stick?

If it's ext2, it may be that you have the immutable flag set on the file, or the directory containing it.

try using
```
lsattr extlinux.sys
lsattr -d /path
```
where path is again the path to the directory containing extlinux.sys
If either of those outputs something like:
```
----i------------- extlinux.sys
```
then you have an immutable flag set, which you can remove using (eg)
```
sudo chattr -i extlinux.sys
```



That did the trick cheers!

---

