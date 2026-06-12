---
title: "NFS mount nuisance"
date: 2006-09-08
forum: Desktop Environments
---

### Post by caspian154 on 2006-09-08
I am mounting a vfat partition on a local server and trying to mount THAT through NFS on a local laptop, but running into a minor annoyance.

When files are created on the nfs mount from the laptop, it gives an error.

The odd part is that the file is created and if the command is tried again, it works fine - so i would assume that it's a permissions issue.
ie:

```

scott@scott-laptop:~$ cp ls.txt /mnt/storage/
cp: cannot create regular file `/mnt/storage/ls.txt': Operation not permitted
scott@scott-laptop:~$ cp ls.txt /mnt/storage/
scott@scott-laptop:~$

```

I've tried several options with the nfs mount to no avail. I've tried creating files with sudo, negative again. I also have made my uid and guid the same as a user on the server and using nouid or uid options. 

Here's how I'm mounting things:

server (192.168.1.44) /etc/fstab:
```
/dev/hdb1               /storage                vfat    umask=0000      0 0
```

server (192.168.1.44) /etc/export
```
/storage 192.168.1.10(rw)
```

laptop (192.168.1.10) /etc/fstab:
```
192.168.1.44:/storage /mnt/storage nfs noauto,rw,exec,nolock 0 0
```

Has anyone seen a similar issue? or have any suggestions?
Thanks a lot,
Scott

---

### Post by whizbaby on 2006-09-08
Try
/dev/hdb1 /storage vfat defaults,uid=007,gid=46 0 0
in fstab (with, of course, doing **sudo mount -a** after changing)

---

### Post by caspian154 on 2006-09-08
Thank you for your help...

First I should be more clear, sorry... The vfat mount on the server works appropriately. When I'm logged in as a user, I can make and modify files without a hitch. I tried changing my fstab to what was suggested and I could no longer modify the files as a user, nor could I create files when I nfs mounted them either. 

(the server is fedora core 5 - not ubuntu, which is probably why mounting with those options didn't work). 

With that said, I also noticed a new issue... I think that the error occurs when the cp command is setting the permissions on the file, because I receive the same error when I chmod the file (Operation not permitted). Here's an example:

```
scott@scott-laptop:/mnt/storage$ ls -l /home/scott/ls.txt
-rw-r--r-- 1 scott scott 7739 2006-09-08 15:14 /home/scott/ls.txt
scott@scott-laptop:/mnt/storage$ cp /home/scott/ls.txt .
cp: cannot create regular file `./ls.txt': Operation not permitted
scott@scott-laptop:/mnt/storage$ ls -l ls.txt
-rwxrwxrwx 1 root root 0 2006-09-08 20:26 ls.txt
scott@scott-laptop:/mnt/storage$ chmod 655 ls.txt
chmod: changing permissions of `ls.txt': Operation not permitted

```

How do I tell the mounted partition not to preserve permissions? can I? Can I explicitely set what I want the permissions to be within the fstab?

---

### Post by whizbaby on 2006-09-08
EDIT: removed for deeper consideration.

---

### Post by whizbaby on 2006-09-08
Sorry, you cannot mount a vfat partition with nfs, it's meant to share linux file-systems. You will have to use samba (don't use that personally so it took a while 'till the enlightenment came). For samba this seems getting the point:
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

(sorry again for taking so long)

---

### Post by caspian154 on 2006-09-08
No problem, thank you so much for your help! I'll probably reformat the disk using ext, if I can back up all the data in the meantime... I have been using a fat partition just in case I need to use it an usb enclosure, which I'm thinking is not worth this headache!

anyway, thanks a lot!

---

### Post by Rogg on 2006-09-10
I always thought permissions errors on vfat/fat were normal when copying from unix, as the filesystem doesn't support full permissions.

Just my 0.02 eurocents.

---

### Post by whizbaby on 2006-09-10
No, this can be resolved by mounting vfat with some special options (e.g. umask).

---

