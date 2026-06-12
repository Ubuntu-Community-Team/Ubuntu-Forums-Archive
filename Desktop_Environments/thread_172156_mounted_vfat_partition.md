---
title: "mounted vfat partition ?"
date: 2006-05-08
forum: Desktop Environments
---

### Post by choub08 on 2006-05-08
I have setup a fat32 partition to exchange data between windows Xp and Ubuntu.
I mounted it with the line :
/dev/hda7       /sharewin       vfat    iocharset=utf8,umask=0222  	 0       0
in my /etc/fstab file and it works. However, the mounted media is not visible on gnome desktop... do you know how to solve this issue.
thanks 
F.

---

### Post by aysiu on 2006-05-08
Go to a terminal and copy and paste this command: ```
ln -s /sharewin ~/Desktop/sharewin
```

---

### Post by choub08 on 2006-05-11
[QUOTE=aysiu]Go to a terminal and copy and paste this command: ```
ln -s /sharewin ~/Desktop/sharewin
```[/QUOTE]

Thanks 8) 
F.

---

