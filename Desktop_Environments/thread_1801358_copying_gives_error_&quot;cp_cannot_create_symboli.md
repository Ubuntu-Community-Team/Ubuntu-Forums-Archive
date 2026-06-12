---
title: "copying gives error &quot;cp: cannot create symbolic link&quot;"
date: 2011-07-10
forum: Desktop Environments
---

### Post by bwanaaa on 2011-07-10
i am root
i have an ext4 partition of a usb drive mounted at /mnt/sdc1
i have fat32 partition of the same drive mounted at /mnt/sdc3


i want to copy the folder /mnt/sdc1/mnt/dir to /mnt/sdc3
i navigate to /mnt/sdc3

i type this in terminal
cp -r /mnt/sdc1/mnt/dir .

I get a lot of this
cp: cannot create symbolic link

How do i copy something from an ext4 partition to a fat32 partition?

---

### Post by matt_symes on 2011-07-10
Hi

Fat32 does not support symbolic links are far as i am aware.

Try

```
cp -r /mnt/sdc1/mnt/dir/* .
```

Kind regards

---

### Post by bwanaaa on 2011-07-10
I should add one detail. The folder I am trying to copy has root permissions (created on another linux box) and even though I am root on this box, I do not have access to it. (Not even read permissions!) 

I realize that I could chmod +rwx the directory, but I do not want to screw up the permissions of the files so that they are not readable on the original linux box.

Actually, the directory I am trying to copy is a Linux installation so I am afraid to muck it up lest it become unbootable.

---

### Post by bwanaaa on 2011-07-10
I repartitioned my drive and created another ext4 partition. it works fine now. tnx.

---

