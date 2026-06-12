---
title: "Trying to mount Fat32 partitions"
date: 2005-08-21
forum: Desktop Environments
---

### Post by crt on 2005-08-21
Hello, I'm simply trying to mount my other partitions on my computer so I have access to my other drives, the problem is I don't have permission to modify the fstab file. I've searched the forums and search the unoffficial user guide and followed the instruction to enable root login. But it will not allow me to do that. I've use sudo I've used everything suggested in the forums and the user guide. But the system is so locked down I am unable to do anything.
I understand the idea behind not allowing alterations to the OS config files, but I can't do anything.
I've tried modifying the kdmrc file and I don't have permision to do that. 
And I have no idea how to allow permission to modify the config files other than root login.
So I'm at a loss as to what else to do.
I hope the developers of kubuntu lighten up on the security restrictions in the release of breezy badger. Maybe put some sort of error checking or have lots of warnings popup before the person toasts their system.

R

---

### Post by amastronardi on 2005-08-21
```
sudo vi /etc/fstab
```

---

### Post by SGC on 2005-08-21
Hit ALT+F2  in your keyboard and then type
```
kdesu kate /etc/fstab
```

Or browse to /etc/ in konqueror, and right click on fstab and choose:
Actions -> Edit as Root

---

### Post by crt on 2005-08-22
Cool kdesu kate /etc/fstab worked, but sudo vi didn't work. 

Thanks, will add this to my how-to list

R

---

