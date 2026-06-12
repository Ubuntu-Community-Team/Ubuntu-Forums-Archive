---
title: "chown problem"
date: 2006-05-31
forum: Desktop Environments
---

### Post by yyagol on 2006-05-31
Hi
i have a vfat partition that i want to mount to /home/yyagol/dtd
i did this :
#mount -t vfat -o defaults,umask=oooo /dev/sda2 /home/yyagol/dtd

so far so good now the problen is that im not the owner of this dir.
before mounting i was the owner and after mounting root is the owner
when i try to chown yyagol /home/yyagol/dtd 
i get permition denay ...how can i change my ownership of this mounted dir ?

---

### Post by chriscando on 2006-05-31
Try the same command using sudo.
sudo chown yyagol /home/yyagol/dtd
this way you are chaning the permissions as a super user rather than your normal account.

---

### Post by aysiu on 2006-05-31
You can't *chown* FAT32.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by yyagol on 2006-06-01
i did it all as root # ... no need for sudo
what i did also whas uid=yyagol and i got this :
```
 # ls -l
total 28
drwxr-xr-x  2 yyagol yyagol  4096 2006-05-31 21:00 Desktop
drwxrwxrwx  4 yyagol root   16384 2006-05-31 22:03 dtd
drwxr-xr-x  5 yyagol yyagol  4096 2006-05-31 18:46 install
drwxr-xr-x  2 yyagol yyagol  4096 2006-05-31 18:12 pics
```
it looks ok but its not . i can creat empty file to this dir
as 'user' but when Azureus try to write it say permition denay
Azureus can write to /home/yyagol and the only difrent is
the mount owner.

---

### Post by yyagol on 2006-06-01
Well ifound another thing about this prolem
after i mount it i cannot umount 
```
~# mount -t vfat -o uid=yyagol,user,defaults,umask=0000 /dev/sda3 /home/yyagol/dtd/
~# ls -l
total 28
drwxr-xr-x  2 yyagol yyagol  4096 2006-05-31 21:00 Desktop
drwxrwxrwx  3 yyagol root   16384 1970-01-01 02:00 dtd
drwxr-xr-x  5 yyagol yyagol  4096 2006-05-31 18:46 install
drwxr-xr-x  2 yyagol yyagol  4096 2006-05-31 18:12 pics
~# umount /home/yyagol/dtd/
umount: /home/yyagol/dtd: device is busy
umount: /home/yyagol/dtd: device is busy
```

---

### Post by frodon on 2006-06-01
This may happen if you have an apps opened which use the partition, nautilus for example, so close all the apps and it will work.
You can try the -f option with the umount command to force the unmount but it don't work in all the cases.

Azureus is a special case, read that to use FAT32 partition with azureus : [http://doc.gwos.org/index.php/Making_Azureus_recognize_your_FAT32_partition](http://doc.gwos.org/index.php/Making_Azureus_recognize_your_FAT32_partition).

Your umask option should be : **umask=000** and not umask=000**0**
In addition it seems you used "o" character instead of "0" character with the umask command, maybe it's a typo in your post.

---

