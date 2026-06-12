---
title: "samba mounting problem.."
date: 2005-06-20
forum: Desktop Environments
---

### Post by kimes on 2005-06-20
I have another windows machine so I wanna connect them..

I installed samba stuff and set it up..
Actually It works with smbmount command. But I need more convenient way to do it
So I added some lines like this

```
//bektekcom/hdd	/mnt/vm			smbfs	rw,user,noauto,iocharset=cp949	0	1
``` 

And I run this command with normal user privelige.

```
mount /mnt/vm 
or smbmnt /mnt/vm
``` 

It should works, with this like other windows partitions..
But I got error message which tells 'Operation is not permmited'

How could I fix that?

---

### Post by sinbad782 on 2005-06-20
I have had similar trouble with this - normal users not being permitted to mount SMB shares. I was using SMB4K in KDE to browse available shares, but it seemed that mounting these was not permitted. 

 think the solution is to change the permissions on the smbmnt command to allow use by normal users. From a terminal, try giving it a 

sudo chmod +s /usr/bin/smbmnt

this should then allow non-root users to mount shares.

---

### Post by kimes on 2005-06-20
[QUOTE=sinbad782]I have had similar trouble with this - normal users not being permitted to mount SMB shares. I was using SMB4K in KDE to browse available shares, but it seemed that mounting these was not permitted. 

 think the solution is to change the permissions on the smbmnt command to allow use by normal users. From a terminal, try giving it a 

sudo chmod +s /usr/bin/smbmnt

this should then allow non-root users to mount shares.[/QUOTE]
 I tried that . but doesn't work..
Any other idea?

---

### Post by sinbad782 on 2005-06-20
I'm not sure what else it could be, but you could try using the smbmount command instead of smbmnt and seeing if that makes any difference.

---

### Post by sinbad782 on 2005-06-20
Here's my reference:

[http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html](http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html)

---

