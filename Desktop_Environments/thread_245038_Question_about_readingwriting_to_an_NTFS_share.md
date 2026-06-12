---
title: "Question about reading/writing to an NTFS share"
date: 2006-08-27
forum: Desktop Environments
---

### Post by lzydba on 2006-08-27
Hi all,

I was browsing through some of the HOWTOs and I keep seeing posts about how to set up NTFS mounts that will allow for read and write, and that it is an experimental thing to do with linux.

I am still a linux newbie but I have run Fedora and Slackware boxes before and I always just used smb to mount my network shares that run on a Win2k3 server, and never had any problems reading or writing to those shares. I never used any of the methods that I am reading about here, or ever experienced the inabilty to write to those shares like I read about here.

My question is am I taking a risk with my data by using smbmount? Can it get corrupted somehow doing this?

---

### Post by givré on 2006-08-27
When you use partition through a network, it's a always the host system (in the sense host of the files) who do the operation. So if you write to an NTFS partition manage by windows, it's actually windows which will write ont it and not linux.
So yeah it's totaly safe.

---

### Post by Cynical on 2006-08-27
Either those shares are not ntfs or write support was added to the version of fedora or slackware you were running. Read support has never been an issue. Of course your data **can** become corrupted, but since you don't know how ntfs write support is implemented in your setup, its hard to say exactly how safe it is. 

Try doing
> cat /etc/fstab
on your setup and post the output here

---

### Post by lzydba on 2006-08-27
The shares are most definately NTFS. I never added any NTFS write support to Slackware, which I'm pretty sure would not have it unless I put it there. Can't say the same about Fedora.

I also use the same method with Ubuntu, and I never used anything to add NTFS write support specifically here. I just installed smbfs with sudo apt-get install smbfs, and then add my shares to my fstab file, that's all.

My fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda2       /boot           ext2    defaults        0       2
/dev/sda5       /home           ext3    defaults        0       2
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda3       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
//fileserver/netstore1 /mnt/fileserver/netstore1 smbfs credentials=/home/MYUSER/.smbcredentials,workgroup=MYDOMAIN,ip=xxx.xxx.x.xxx,uid=myuser,gid=users 0 0
//fileserver/netstore2 /mnt/fileserver/netstore2 smbfs credentials=/home/MYUSER/.smbcredentials,workgroup=MYDOMAIN,ip=xxx.xxx.x.xxx,uid=myuser,gid=users 0 0
//fileserver/netstore3 /mnt/fileserver/netstore3 smbfs credentials=/home/MYUSER/.smbcredentials,workgroup=MYDOMAIN,ip=xxx.xxx.x.xxx,uid=myuser,gid=users 0 0

---

### Post by givré on 2006-08-27
Just before
> When you use partition through a network, it's always the host system (in the sense host of the files) who do the operation. So if you write to an NTFS partition manage by windows, it's actually windows which will write on it and not linux.
So yeah it's totaly safe.

---

### Post by lzydba on 2006-08-27
I saw your's Givre, and that seems to make more sense to me. I was replying to Cynical's post.

So I take it from what you wrote that the HOWTOs and such I read about here are directed at people that want to host an NTFS share on their linux systems? Rather than people that have NTFS shares on separate windows systems that they want to connect to with their linux system.

---

### Post by Cynical on 2006-08-27
Oh yeah you're right, I misread that.

---

