---
title: "nfs - problems (i thought it'd be pretty straight fwd..)"
date: 2006-04-14
forum: Desktop Environments
---

### Post by dotdot on 2006-04-14
hi folks - i have a small (ok it doesn't work.. yet) problem with nfs.

two laptops.
a/ server - with (sudo apt-get install portmap nfs-kernel-server) installed.
modded fstab 
exported fs all ok..
b/ client with (sudo apt-get install portmap nfs-common) installed.
modded fstab
...
both boxes can ping each other...
both hosts files have the other ip / names inside...

...
on box b - trying to .. mount the other fs which has been exported...
i get 

mount: RPC: Program not registered


- i was following through ..
[https://wiki.ubuntu.com/SettingUpNFSHowTo?highlight=%28nfs%29](https://wiki.ubuntu.com/SettingUpNFSHowTo?highlight=%28nfs%29)
however there's no troubleshooting section.

..anyone have some suggestions - I'm sure I'm missing something simple.

..cheers
..

(if you req any further detail - let me know..):rolleyes:

---

### Post by pietro_spina on 2006-04-14
did you make the mount point for your fstab entry? (you didn't mention)
restart all the appropriate services?

also, can you share the exports entrys and fstab and hosts.allow hosts.deny all those entrys... maybe you made a typo...

-p

---

### Post by dotdot on 2006-04-14
hi - yes i editted the fstab file on box b
looks like

# ubux
ubux:/other /mnt  nfs rw,hard,intr 0 0

exports on box a

/other @fugubu(rw,sync)

have restarted a and b

now i'm getting...

$ sudo mount /mnt                 
mount: ubux:/other failed, reason given by server: Permission denied

- can't be far away now... ? ideas ?

..

---

### Post by pietro_spina on 2006-04-14
does your host name actually have an "@" sign in it? I don't know if that is a good idea or not.
and are you really trying to share a directory at "/other" are the permissions set properly

The way I have it set is to have a folder "share" that has permissions set to 777

each user can manage their own files permissions...
I bet if you created a folder as root at "/other" it has restrictions that don't allow others to read/write...

I have no clue about the security of these permissions though.
I trust my 2 users... me and GF....

-p

---

### Post by pietro_spina on 2006-04-14
And I'd probably change the mount point to something like 
/mnt/other

rather that just /mnt    because you will probably have more mount points in the future...

then you would do

$ sudo mount /mnt/other

---

### Post by dotdot on 2006-04-14
ok i've changed the mount point on b to /nfs_mount for simplcity.
I've changed the perms on it to 777

I've restarted on a and b...

now i get...

$ sudo mount /nfs_mount
mount: can't get address for ubux

fstab (on b) looks like :
# ubux
ubux:/other /nfs_mount  nfs rw,hard,intr 0 0

address ?

---

### Post by pietro_spina on 2006-04-14
I'm going to go back to my firs question and elaborate a bit.
Did you make the mount point?
What I mean is does the directory "/nfs_mount" exist?
This command should make it for you in the /mnt directory because that is really where you should mount it. 
```
sudo mkdir /mnt/nfs_share
```

Make fstab (on b) looks like :
```
ubux:/other /mnt/nfs_share nfs rw,hard,intr 0 0
```
Then
```
sudo mount /mnt/nfs_share
```

---

### Post by cubeice24 on 2006-04-26
I'm running Hoary and here's the list of things I did on my **server** machine in order to get a succesful mount:
1)apt-get-installed *portmapper*, *nfs-common* and *nfs-kernel-server*
2)edited /etc/exports : /home/ez/Shared 139.8.8.25(rw)
3)restarted the following services:
   /etc/init.d/portmap restart
   /etc/init.d/nfs-common restart
   /etc/init.d/nfs-kernel-server restart

---

