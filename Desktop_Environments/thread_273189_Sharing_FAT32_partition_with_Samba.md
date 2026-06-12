---
title: "Sharing FAT32 partition with Samba"
date: 2006-10-07
forum: Desktop Environments
---

### Post by n7cee on 2006-10-07
I've finally succeeded after much ](*,) in using Samba to share a FAT32 partition on my desktop machine (running Dapper) so it can be read and written by an ordinary Dapper user on my notebook, as well as from Windows XP. I found various posts that pointed me in the right direction, but I thought it might be useful to put the info in one post.

Because my work requires several Windows programs that have no Linux equivalent (Adobe Illustrator and National Geographic Topo, among others), I sometimes have to reboot into Windows XP either on my notebook or desktop. (I'm testing these apps on Win XP on VMWare at the moment. The Samba share works with VMWare as well.)

I have data that I need to use from both Dapper and Windows on a FAT32 partition, hda5.

On the desktop (server) machine (named terra), /etc/fstab has the following line:

```
/dev/hda5 /media/hda5 vfat umask=0000 0 0
```

/etc/samba/smb.conf has has the following section:

```
[HDA5]
path = /media/hda5
guest ok = yes
read only = no
case sensitive = no
msdfs proxy = no
```

The notebook (client) machine has the following line in /etc/fstab:

```
//terra/HDA5	/mnt/TERRA_HDA5	smbfs smbpasswd,uid=1000,gid=1000 0 0
```

I can read and write to this share from Dapper or Windows XP on the notebook, and from VMWare on the desktop. :)

---

### Post by lemonsCC on 2006-10-07
when I try to connect to my FAT32 partition from OS X I type: 
```
smb://192.168.1.10x/hda5
```
It askes me for a user name and pass..I tried my Ubuntu user name and pass and it refused it...what did you use?

---

### Post by n7cee on 2006-10-07
Dapper just asks for a password, and accepts my regular user password.

---

