---
title: "problem changing directory ownership"
date: 2006-02-17
forum: Desktop Environments
---

### Post by bailout on 2006-02-17
I have a fat32 partition which I enabled according to the ubuntu guide by adding the following to fstab

/dev/hda5	/mnt/data	vfat	umask=000	0	0

It has a folder on it with photos in it. I am trying to get digikam to use this folder but keep getting an error msg saying that digikam does not have write permission to the folder. ls -l gives the following

drwxrwxrwx  22 root root  8192 2005-10-07 09:32

Now from what I understand that means that the folder is owned by root but everyone can read or write to it. 

Thinking that digikam might be objecting because the files are owned by root I tried changing the ownership to me as a user with the following

sudo chown me ./photos/

but got the following msg

chown: changing ownership of `./photos/': Operation not permitted

Why won't it let me change the ownership?

---

### Post by Lanrond on 2006-02-17
[QUOTE=bailout]I tried changing the ownership to me as a user with the following

sudo chown me ./photos/

but got the following msg

chown: changing ownership of `./photos/': Operation not permitted

Why won't it let me change the ownership?[/QUOTE]

Excuse me for the trivial question, but is user *me* configured? :)

---

### Post by bailout on 2006-02-17
Not sure I understand, even if it is a trivial question :confused:  I mean my normal user account.

---

### Post by yota on 2006-02-17
Fat filesystem does not support owner:group attributes... (Hey, is the filesystem on wich ran Ms-DOS: how can it work?!? ;) ) so the behaviour of chown is normal.

Try to mount the filesystem read-write with the 'rw' option; if it does not work, test if root can write to that partition and post here.

Hope this helps!

---

### Post by joselin on 2006-02-17
Use this in your /etc/fstab:

> /dev/hda5 /mnt/data vfat   auto   rw,user,noauto   0   0

For more info:

> man fstab

Regards.

---

### Post by bailout on 2006-02-17
thanks for the replies. I will check out the extra info on the fstab settings.

For now I have got digikam to use the folder by "chmod"ing the folder to 777.

thanks again

---

