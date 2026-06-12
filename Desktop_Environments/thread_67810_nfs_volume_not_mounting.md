---
title: "nfs volume not mounting"
date: 2005-09-21
forum: Desktop Environments
---

### Post by holiday on 2005-09-21
My 5.1 ubuntu laptop can't mount a drive on my FC2 box. 

root@ubuntu:~# mount //192.168.0.100/home/stephen /home/stephen/sroom -o username=xxxxx,password=yyyyyyy

gets this error

mount: wrong fs type, bad option, bad superblock on //192.168.0.100/home/stephen,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


Ok.

So dmesg has this
[ 2984.325346] RPC: failed to contact portmap (errno -5).
[ 4372.429140] nfs warning: mount version older than kernel
[ 4800.887360] nfs warning: mount version older than kernel
[ 4835.815209] portmap: server localhost not responding, timed out
[ 4835.815238] RPC: failed to contact portmap (errno -5).
[ 4870.742767] portmap: server localhost not responding, timed out
[ 4870.742795] RPC: failed to contact portmap (errno -5).
[ 4905.670625] portmap: server localhost not responding, timed out
[ 4905.670653] RPC: failed to contact portmap (errno -5).
[ 7892.831397] smbfs: mount_data version 1919251317 is not supported

Ok - but: 

- portmap is running
root@ubuntu:~# ps aux | grep portmap
daemon   11064  0.0  0.1   1664   456 ?        Ss   06:31   0:00 /sbin/portmap
root     11077  0.0  0.1   1624   496 pts/1    R+   06:31   0:00 grep portmap


- /etc/exports on the host machine is correct (worked for my previous laptop with same ip)

- and the host responds to ping

---

### Post by mlomker on 2005-09-21
> 
mount: wrong fs type, bad option, bad superblock on //192.168.0.100/home/stephen,


It's just a syntax problem.  The **//** shouldn't be in there.  The man page suggests putting the -o before the device and mount point, but I don't know if that matters.

```

mount 192.168.0.100:/home/stephen /home/stephen/sroom 

```

---

### Post by aragorn2909 on 2005-09-21
[QUOTE=holiday]My 5.1 ubuntu laptop can't mount a drive on my FC2 box. 

root@ubuntu:~# mount //192.168.0.100/home/stephen /home/stephen/sroom -o username=xxxxx,password=yyyyyyy

gets this error

mount: wrong fs type, bad option, bad superblock on //192.168.0.100/home/stephen,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


Ok.

So dmesg has this
[ 2984.325346] RPC: failed to contact portmap (errno -5).
[ 4372.429140] nfs warning: mount version older than kernel
[ 4800.887360] nfs warning: mount version older than kernel
[ 4835.815209] portmap: server localhost not responding, timed out
[ 4835.815238] RPC: failed to contact portmap (errno -5).
[ 4870.742767] portmap: server localhost not responding, timed out
[ 4870.742795] RPC: failed to contact portmap (errno -5).
[ 4905.670625] portmap: server localhost not responding, timed out
[ 4905.670653] RPC: failed to contact portmap (errno -5).
[ 7892.831397] smbfs: mount_data version 1919251317 is not supported

Ok - but: 

- portmap is running
root@ubuntu:~# ps aux | grep portmap
daemon   11064  0.0  0.1   1664   456 ?        Ss   06:31   0:00 /sbin/portmap
root     11077  0.0  0.1   1624   496 pts/1    R+   06:31   0:00 grep portmap


- /etc/exports on the host machine is correct (worked for my previous laptop with same ip)

- and the host responds to ping[/QUOTE]


Couple of things, it looks like (and I'm a complete noob) that your syntax on the mount command is a little off.  Shouldn't it be ```
 mount 192.168.0.100:/home/stephen /home/stephen/sroom -o
``` with the colon in there?  Secondly, the "mount version older than kernel" just means you need to upgrade your mount package.  Hopefully this helps.

A

---

### Post by holiday on 2005-09-21
[QUOTE=aragorn2909]Couple of things, it looks like (and I'm a complete noob) that your syntax on the mount command is a little off.  Shouldn't it be ```
 mount 192.168.0.100:/home/stephen /home/stephen/sroom -o
``` with the colon in there?  Secondly, the "mount version older than kernel" just means you need to upgrade your mount package.  Hopefully this helps.

A[/QUOTE]
 Ok - using this 

mount -t nfs 192.168.0.100:/home/stephen /home/stephen/sroom

I reduce the errors to 

7930.512510] nfs warning: mount version older than kernel

What *do* I upgrade? Anyone know the package name?

I suspect it's some other error though.

---

### Post by mlomker on 2005-09-21
> What *do* I upgrade? Anyone know the package name?


It's **nfs-common**.  Are you running the stock kernel?

---

### Post by holiday on 2005-09-21
[QUOTE=mlomker]It's **nfs-common**.  Are you running the stock kernel?[/QUOTE]
 # uname -a
Linux ubuntu 2.6.12-8-386 #1 Thu Sep 15 21:14:32 UTC 2005 i686 GNU/Linux

# apt-get upgrade nfs-common 

gives 

0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.

(The not upgraded ones are evolution -- which I do not like)

---

### Post by holiday on 2005-09-21
[QUOTE=holiday]# uname -a
Linux ubuntu 2.6.12-8-386 #1 Thu Sep 15 21:14:32 UTC 2005 i686 GNU/Linux

# apt-get upgrade nfs-common 

gives 

0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.

(The not upgraded ones are evolution -- which I do not like)[/QUOTE]
 But - hey - 

apt-get install nfs-common

made stuff happen.

However

#mount -t nfs 192.168.0.100:/home/stephen /home/stephen/sroom

still has no good effect.

---

### Post by mlomker on 2005-09-21
> still has no good effect.

Could be a breezy bug.  We'll see if someone else has input.  I confirmed the syntax on my Hoary box this morning.

---

### Post by holiday on 2005-09-21
[QUOTE=mlomker]Could be a breezy bug.  We'll see if someone else has input.  I confirmed the syntax on my Hoary box this morning.[/QUOTE]
 Ok, thanks for your help. 

May I try on other lists/forums or would that be rude?

---

### Post by aragorn2909 on 2005-09-22
My home network, I have 2 Ubuntu boxes networked with NFS.  I have installed both nfs-common and nfs-kernel-server (wouldn't work with just one for some reason) on both boxes.  My /etc/exports file has only one line 
```
/home     192.168.254.1(rw)
```and ```
/home     192.168.254.2(rw)
``` (simple setup, no messing around with /etc/hosts.allow/deny).  A quick reboot to get all the services running, and one command to mount ```
sudo mount 192.168.254.1(and 2) /mnt/home
``` with no extra syntax, and i'm up and running.  If you haven't seen it already [this site](http://www.faqs.org/docs/Linux-HOWTO/NFS-HOWTO.html#REMOTEMOUNT) helped me troubleshoot some problems, perhaps it could help you here?  As for the "mount version older than kernel" error, the package that I believe needs updating is actually called "mount".  Once again, I hope this helps.

A

---

### Post by holiday on 2005-09-22
[QUOTE=aragorn2909]My home network, I have 2 Ubuntu boxes networked with NFS.  I have installed both nfs-common and nfs-kernel-server (wouldn't work with just one for some reason) on both boxes.  My /etc/exports file has only one line 
```
/home     192.168.254.1(rw)
```and ```
/home     192.168.254.2(rw)
``` (simple setup, no messing around with /etc/hosts.allow/deny).  A quick reboot to get all the services running, and one command to mount ```
sudo mount 192.168.254.1(and 2) /mnt/home
``` with no extra syntax, and i'm up and running.  If you haven't seen it already [this site](http://www.faqs.org/docs/Linux-HOWTO/NFS-HOWTO.html#REMOTEMOUNT) helped me troubleshoot some problems, perhaps it could help you here?  As for the "mount version older than kernel" error, the package that I believe needs updating is actually called "mount".  Once again, I hope this helps.

A[/QUOTE]
 Hm. My other box is FC2 and though that's pretty old these days, I don't want to mess with it. It is working. 

I wonder if the two nfs versions are not getting along. That would be bad. I shouldn't have to configure a server to suit its clients. 

I just installed nfs-kernel-server but it did not start because I have no exports from this laptop.

I try apt-get upgrade mount and it tries to install evolution!

Which I do not  want. It seems determined to get on here though.

Thanks for thehelp.

---

