---
title: "Mounting different Windows shares"
date: 2006-09-04
forum: Desktop Environments
---

### Post by uwe on 2006-09-04
I'm trying to mount different Windows Network-Shares with my ubuntu 6.06.

Therefore I have first installed smbfs:
$ sudo apt-get install smbfs

Next I tried to mount a share in the following way:

mount -t smbfs -o username=thename,password=thepw,uid=myubuntuusername, rw //servername/sharename ~/mnt/winsharexy

This works fine, but only with root or using sudo.

Because I work at different customers, I will create simple shell-scripts to mount the necessary shares in my ~/mnt folders.
So I don't want to use root or sudo everytime.

Next I tried "chmod +s" for mount, smbmount and smbmnt, so that I can use the mount-command without root, but I still get the message "only root can do that".

Any ideas?

---

### Post by uwe on 2006-09-12
Really no ideas out there? 

OK - I've helped myself with the following:

Setting the setuid-Bit for /bin/mount didn't work, I still get:
mount: only root can do that

I set the setuid-Bit for smbmnt and smbumount:

**$ sudo chmod u+s /usr/bin/smbmnt**
**$ sudo chmod u+s /usr/bin/smbumount**

Now I can use the smbmount and smbumount as a user without root-privileges. Helpful for me are scripts to mount SMB-Shares from different Windows machines like:

[INDENT][B]...
mkdir ~/mnt/winserver
mkdir ~/mnt/winserver/c$
smbmount //winserver/c$ ~/mnt/winserver/c$ -o username=thename,password=thepw,fmask=755,dmask=755,rw
...[/B][/INDENT]

To unmount them I use another script:
[INDENT]
[B]...
smbumount ~/mnt/winserver/c$
rmdir ~/mnt/winserver/c$
rmdir ~/mnt/winserver
...[/B][/INDENT]

---

