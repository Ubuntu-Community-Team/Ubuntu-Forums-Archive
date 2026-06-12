---
title: "Can't write on ext3, or fat32"
date: 2006-08-18
forum: Desktop Environments
---

### Post by goldencako on 2006-08-18
Hey, I am fairly new to Linux, and a total newbie with Ubuntu. I installed it today, everything went fine, no problems with anything. However, I haven't been able to write to my FAT32 partition, which doesn't have windows, it's only storage. I looked all over the web to find a solution but none worked. I tried changing fstab to everything I could, mounted it and unmounted it a couple of times, and changed permissions more than a few. None worked. Root and normal users can read, and can create new files, however neither can edit the files that are already there. Furthermore, even if I copy a file from my vfat partition to my root desktop, I still cant edit it. Something else that ahs happened was that all of a sudden the mouse clicks and keyboard stopped working (the mouse could still move) and colored vertical lines appeared all over my screen. Only way to solve that was by restarting. This had happened several times with SuSE 9.3 and I wasn't able to fix it. Well, I hope anyone can help me solve any of these two problems. Thanks in advance.

---

### Post by taurus on 2006-08-18
What does your /etc/fstab look like then?  From a terminal (Applications -> Accessories -> Terminal), type

```
more /etc/fstab
```

---

### Post by dannyboy79 on 2006-08-18
I can see how this would be frustrating. My vfat partition is mounted via this fstab entry, /dev/hda5       /windows        vfat    defaults,utf8,umask=007,gid=46 0       1
It's on 2 lines because I copied and pasted right from my fstab file. As far as not being able to write to the file when you copied onto a ext3 filesystem I have no idea whats up with that. What are the permissions of the file?

---

### Post by goldencako on 2006-08-19
Hey, sorry for the trouble, but I figured out the problem. I was only testing this one txt file which i had no permission to write on. So now its all good. Sorry for the troublem thanks

---

