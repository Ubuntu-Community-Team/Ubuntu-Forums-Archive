---
title: "Accesing Hard Drives as normal user"
date: 2005-04-18
forum: Desktop Environments
---

### Post by kenthar on 2005-04-18
Hello

I am new to Ubuntu (and Kubuntu) and have a nasty problem with my hard drives. 
I have 2 hard disks: a 40GB one, partitioned with 30 GB for winxp, 9GB for linux (Kubuntu) and 500MB as swap. The other one is a 80GB unit. 

During the installation progress, the windows partition and the 80GB drive were neither recognized nor configured by the installer. I thought it wasn't a big deal and after the installation I added the windows partition and the 80GB drive to fstab as readable, writable vfat devices.

The windows partition is /dev/hda1, mounted as /media/master.
The 80GB drive is /dev/hdb1, mounted as /media/storage

I can read those drives perfectly. However, I seem to be unable to write to them, even as root (with "sudo"). I tried changing the permissions of the mount points with "chmod a+rw /media/storage". This doesn't return any errors, but it just won't affect the permissions. I am unable to write to those places.

It is a big deal for me, because the 80GB drive was my common storage place for windows and linux (previously, I had suse 9.1 installed). 

Any suggestions will be greatly appreciated. Thanks.

---

### Post by TravisNewman on 2005-04-18
try this as your fstab line-- it's the only way I could get it to work for me, though most people say it's overkill, it works.

/dev/hdb1  /windows  vfat  rw,user,uid=1000,gid=1000,umask=0000  0  0

---

### Post by kenthar on 2005-04-18
It worked just fine.

Thanks a lot!!!  :) 

I suspect that the thing that did the trick was the GID part, 'cause the default user created by ubuntu has a group id of 1000. Is that the cause?

Again, i'm grateful. These forums are great.

---

