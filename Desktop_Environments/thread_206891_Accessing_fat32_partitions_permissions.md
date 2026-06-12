---
title: "Accessing fat32 partitions permissions"
date: 2006-06-30
forum: Desktop Environments
---

### Post by Boomy on 2006-06-30
How can I set a fat32 partition so that I can read and write to it with ubuntu? Right now I'm having trouble even accessing the drive. My removable drive fat32 works perfectly, but not my 2nd internal drive or other partitions on my main drive.

---

### Post by taurus on 2006-06-30
You need to edit your /etc/fstab and set the permission in there.  You should have a line that looks something like
```

/dev/hda2     /share     vfat     defaults,umask=00000     0     0

```

---

### Post by Boomy on 2006-06-30
It doesn't seem to make a difference what I put in fstab. Right now I have something like this in there. 

/dev/sda3 /media/hda3 rw,umask=0000,user,gid=users 0 0

---

### Post by taurus on 2006-06-30
[QUOTE=Boomy]It doesn't seem to make a difference what I put in fstab. Right now I have something like this in there. 

/dev/sda3 /media/hda3 rw,umask=0000,user,gid=users 0 0[/QUOTE]
Have you tried
```

/dev/sda3     /share     vfat     defaults,umask=0000     0     0

```
Of course, don't forget to create a mount point /share first...
```

sudo mkdir /share

```

---

### Post by msandersen on 2006-06-30
[QUOTE=Boomy]/dev/sda3 /media/hda3 rw,umask=0000,user,gid=users 0 0[/QUOTE]
Can I assume you have **vfat** in there?
```
/dev/hda3 /media/hda3   vfat   rw,umask=0000,user,gid=users,uid=1000   0   0
```
It shouldn't matter with that umask, but you could try the uid as well (here assuming it's 1000).
Also, is it **s**da3 or **h**da3? It also assumes that you actually have a directory at /media/hda3 (or sda3).
Try mounting it in the terminal and see if there are any specific errors.
```
umount -a ; mount -a
```

---

### Post by msandersen on 2006-06-30
And if it works, try changing the **umask** to **0002** or **0007** depending on what access you want outsiders to have; read-execute-no-write or none.

---

### Post by Boomy on 2006-07-01
Thanks for the help. I don't know what happened, but when I booted u p today, the drive was in "places" and working perfectly. :)

---

