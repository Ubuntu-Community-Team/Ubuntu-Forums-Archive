---
title: "permissions on fat32 drive"
date: 2006-01-16
forum: Desktop Environments
---

### Post by jeremytaylor on 2006-01-16
Hi there, 
I have a couple of fat32 partitions that I use to share data between windows and linux. 
I mount it in the way the ubuntuguide suggests but all my permissions are weird. All the files are owned by root and all are executable. This is a wee bit of a pain.
I've attached my fstab

Can anyone tell me what I've done wrong?
thanks
Jeremy




[ATTACH]5381[/ATTACH]

---

### Post by ubuntuuser on 2006-01-16
FAT32 doesn't support file permissions. If you copy a file on that partition the permissions are lost. And as far as I understand that process of mounting, all files are owned by the user who mounted the disk.

---

### Post by jeremytaylor on 2006-01-16
ahh well i guess that would explain that then... thanks. hmm what a pain
thanks again
Jeremy

---

### Post by aysiu on 2006-01-16
That doesn't explain why they're owned by root, though.
Can you post the contents of your /etc/fstab?

---

### Post by soulestream on 2006-01-16
the reason that everything is owned by root, is that root mounts the drive(i think) and umask=000 says everything is rwx. 

soule

---

### Post by aysiu on 2006-01-16
[QUOTE=soulestream]the reason that everything is owned by root, is that root mounts the drive(i think) and umask=000 says everything is rwx. 

soule[/QUOTE] Gotcha. Thanks for the clarification.

---

