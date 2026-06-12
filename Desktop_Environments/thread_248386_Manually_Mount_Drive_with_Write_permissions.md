---
title: "Manually Mount Drive with Write permissions"
date: 2006-09-01
forum: Desktop Environments
---

### Post by pt123 on 2006-09-01
I need to manually mount as ext2 drive with write permissions.

currently I am doing this 
sudo mount /dev/hda6 /media/d -t ext2

But its only giving me read access to it I can't write to it.

Also I don't want it to to be mounted when I log in, so no fstab solutions.

---

### Post by aysiu on 2006-09-01
Why don't you do this? ```
sudo mount -t ext2 /dev/hda6 /media/d
sudo chown -R pt123:pt123 /media/d
```

---

### Post by pt123 on 2006-09-01
Thanks that did the trick

---

