---
title: "Backup problem with SMB drive"
date: 2006-06-05
forum: Desktop Environments
---

### Post by chloraldo on 2006-06-05
I am using Simple Backup and would like to send my backups to an external drive with the URL smb://192.168.1.37. How can I do that?

Earlier the disk was conntected directly to the PC (USB) and that worked with a symbolic link to the disk. Is it possible to make a symbolic link to smb://192.168.1.37? How?

Thanks!

---

### Post by frying_fish on 2006-06-05
assuming its on another system..

Then just add a line to etc/fstab

that looks similar to :

//computer/share /mount/point smbfs defaults,credentials=/etc/samba/smb.credentials,rw,uid=user 0 0

and make sure you have smbfs installed.

The file smb.credentials should be of the form

username = USER
password = PASSWORD


Then that location will mount every time you boot, or if its not accessible when you boot, it won't, but then if it does become sucessful you can mount it with sudo mount -a

---

### Post by chloraldo on 2006-06-05
[QUOTE=frying_fish]assuming its on another system..

Then just add a line to etc/fstab

that looks similar to :

//computer/share /mount/point smbfs defaults,credentials=/etc/samba/smb.credentials,rw,uid=user 0 0

and make sure you have smbfs installed.

The file smb.credentials should be of the form

username = USER
password = PASSWORD


Then that location will mount every time you boot, or if its not accessible when you boot, it won't, but then if it does become sucessful you can mount it with sudo mount -a[/QUOTE]
It's a Storage System that connects 2 disks to the network. That device has the IP 192.168.1.37. Disk 1 has smb://192.168.1.37/DISK%201.

So mounting Disk 1would be something like this?

//smb://192.168.1.37/DISK%201 /media/disk1 smbfs defaults,credentials=/etc/samba/smb.credentials,rw,uid=user 0 0

---

### Post by frying_fish on 2006-06-05
no, it would be something like this:

//192.168.1.37/DISK%201  ........


the "smb://" is just something that nautilus prefixes so it knows its using the smb protocol, you won't need that in fstab

---

### Post by chloraldo on 2006-06-05
[QUOTE=frying_fish]no, it would be something like this:

//192.168.1.37/DISK%201  ........


the "smb://" is just something that nautilus prefixes so it knows its using the smb protocol, you won't need that in fstab[/QUOTE]
I tried it with this line:
//192.168.1.37/DISK%201/ /media/disk1 smbfs defaults,credentials=/etc/samba/smb.credentials,rw,uid=user 0 0

But I got this error:
12976: tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share name)
SMB connection failed

What's wrong? In Nautilus I still can access the disk...

---

