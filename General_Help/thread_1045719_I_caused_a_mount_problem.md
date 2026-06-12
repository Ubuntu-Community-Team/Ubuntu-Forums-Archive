---
title: "I caused a mount problem"
date: 2009-01-20
forum: General Help
---

### Post by penguinchrissy on 2009-01-20
I tired to change the mount point for my external harddrive and now I get this error 

mount_point cannot contain the following character: newline,G_DIR_SEPARATOR (usually /)

How can I fix this? I feel stupid for breaking something that was working but I was just curious

---

### Post by taurus on 2009-01-20
Did you change it in /etc/fstab?

What are the outputs of these commands from a terminal?

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by penguinchrissy on 2009-01-20
I opened it up with dolphin and that fixed the problem but why did this happen?

---

### Post by mc4man on 2009-01-20
> why did this happen? 

Not sure if you were using nautilus but that error message usually indicates that you changed the mount point of the volume or drive in it's properties and used the full path.

When doing it that way you can only enter the new dir. name and only if it's to be mounted in /media. (or what ever dir .it's in

Ex. 
orig. mount point /media/foo
right way
just enter foo2

wrong way
entering /media/foo2
or /<some other dir.>/foo2

---

