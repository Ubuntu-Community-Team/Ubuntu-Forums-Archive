---
title: "Ownership problems"
date: 2009-02-13
forum: General Help
---

### Post by raveesh on 2009-02-13
Hey,
I am using ubuntu to develop a website using php. 
The problem is that i have  mounted my windows ntfs partition to /media/disk and it contains the directory of my site.

Now, i have tried to change the ownership of /media/disk/wamp/www using chmod as well as chown but if still shows the ownership as root. here is what i did. 

```
sudo chown -cR raveesh mysite
```
 it displayed that all the file ownership had been changed to raveesh.
but on  doing ```
ls -l
``` it still shows it as root!

I ma using ubuntu 8.10
Please help

---

### Post by sisco311 on 2009-02-13
You can't use chown, chmod on fat and ntfs partitions.

You can set the owner/permissions at mount time with the

uid,gid,umask,dmask and fmask mount options. 
```

mount -t ntfs -o defaults,uid=username,gid=groupname,dmask=002,fmask=113 /dev/sdXY /mount/point
```

How do you mount the partition?

---

### Post by raveesh on 2009-02-13
thanks for the reply,
I manually edited the fstab.
I am new to linux. all i did was add these lines to it:

/dev/sda1 /media/disk ntfs-3g defaults,locale=en_IN 0 0
/dev/sda2 /media/Down ntfs-3g defaults,locale=en_IN 0 0

So what do i do to set the permissions.
I wish to grant every user the ability to access  and write to the directory.
so which username/groupname do i use?

---

### Post by sisco311 on 2009-02-13
> /dev/sda1 /media/disk ntfs-3g defaults,gid=46,dmask=002,fmask=113,locale=en_IN 0 0
/dev/sda2 /media/Down ntfs-3g defaults,gid=46,dmask=002,fmask=113,locale=en_IN 0 0

this will set root as owner and plugdev as group(the first user is in the plugdev group by default).

read/write/execute permissions for owner and group on directories
read/write permissions for owner and group on files
read/execute permissions for others on directories
read permission for others on files

[uhelp]community/FilePermissions[/uhelp]
[uhelp]community/Fstab[/uhelp]

You can add a user to the plugdev group with:
```
sudo adduser *username* plugdev
```

---

### Post by raveesh on 2009-02-13
thanks for the help, it worked

---

### Post by raveesh on 2009-02-13
just one more thing i am unable to mark this as solved. there is no such option coming up in the thread tools menu.
(Didn't know where to ask so here it goes)

---

### Post by sisco311 on 2009-02-14
> **raveesh said:**
> just one more thing i am unable to mark this as solved. there is no such option coming up in the thread tools menu.
(Didn't know where to ask so here it goes)

[thread=1039481]Thanks and Solved have been disabled due to problems with the database.[/thread]

---

