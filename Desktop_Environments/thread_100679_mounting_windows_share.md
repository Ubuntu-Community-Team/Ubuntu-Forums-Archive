---
title: "mounting windows share"
date: 2005-12-08
forum: Desktop Environments
---

### Post by Balakrishnan on 2005-12-08
I am new to Ubuntu. I have Ubuntu 4.10 installed in my hard disk.

I have a Windows XP machine which has a "read only" share and  anyone in the Intranet can access it.

I use the following command in some Linux distributions (like Knoppix) to mount this share and it works fine.

However, the same command does not work in Ubuntu. 

Can someone guide me?

Command : (as root in knoppix and sudo in Ubuntu)

     mount -t smbfs -o username="domain\username" //ip_no_of_windows/sharename  /mnt

(when password of Windows is prompted, password is provided. Mounting happens fine in Knoppix but not in Ubuntu 4.10 . Why ?)

I faced similar problem in some other distributions too.

Error reported by Ubuntu 4.10 :
   wrong fs type or bad option or bad superblock on //ip_no_of_windows/sharename or too many mounted file system

I also tried "cifs" instead of "smbfs". Here also no luck.

---

### Post by fourchannel on 2005-12-08
you might try opening up synaptic and look for samba, or smbutils, and install those packages. you don't need the samba server to connect but you probably need the helper packages to mount.

---

