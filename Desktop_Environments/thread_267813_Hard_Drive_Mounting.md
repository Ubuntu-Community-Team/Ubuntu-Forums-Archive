---
title: "Hard Drive Mounting"
date: 2006-09-29
forum: Desktop Environments
---

### Post by wolf202 on 2006-09-29
](*,)

ok so I have 2 HDDs 

HD A is 160 GB - 2 Partitions A-A is 40 GB NTFS(Windows), A-B is 120 GB NTFS
HD B is 300 GB - 2 Partitions B-A is 40 GB Linux, B-B is 250 GB NTFS

ok so in Ubuntu Dapper I can View and Read off all partions except B-B, when I try to access it un "Computer"

I get "Unable to mount selected volume" 
"error: device /dev/hdb2 is not removable 
error: could not execute pmount"

why is this?

-wolf

---

### Post by KingFuzz on 2006-09-29
I've had this problem as well. It's seems ubuntu sometimes believes one of your partitions is a removable drive and tries to mount it with 'pmount' instead of the normal mount-command.. Sadly I'm a noob in this linux world so I cannot help you, only explain it..

---

### Post by anaconda on 2006-09-29
pmount is meant for removable disks, and you want to mount a fixed disk.

Here is how you can mount it manually from terminal:
```
sudo mkdir /storage
sudo mount -t ntfs /dev/hdb2 /storage
```

After that it will be mounted to folder /storage

and if you want it mounted automatically with each boot, then you should edit your /etc/fstab -file.

here is an example line you want to add to your fstab -file
/dev/hdb2 /storage ntfs defaults,nls=utf8,umask=007,gid=46 0 0

---

### Post by KingFuzz on 2006-09-29
Is it possible to make the partion mount by right-clicking on it and selecting "mount"?
I'm just courious, since it mounts using the terminal, but not by using point and click.

---

### Post by wolf202 on 2006-09-29
I did  that and when I navigate to storage I get an error saying I don't have permission.


-wolf

---

