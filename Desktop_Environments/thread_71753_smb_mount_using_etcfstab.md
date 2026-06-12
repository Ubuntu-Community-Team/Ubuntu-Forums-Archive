---
title: "smb mount using etc/fstab"
date: 2005-10-04
forum: Desktop Environments
---

### Post by duffydack on 2005-10-04
Basic install of Kubuntu 5.04, just added linux-686 and gcc
tryin to map a share
//my_win_ip/sharename      /mnt/windows       smbfs username=administrator,password=mypass,uid=1000
(works in suse)
"mount -a" 
and i get

mount: wrong fs type, bad option, bad superblock on //my_win_ip/sharename
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

dmesg | tail says 
smbfs: mount_data version 1919251317 is not supported
smbfs: mount_data version 1919251317 is not supported
smbfs: mount_data version 1919251317 is not supported

---

### Post by Dennis Laumen on 2005-10-04
Hi Duffy,

You need to install the 'smbfs' package.

Good luck & have fun!

---

### Post by duffydack on 2005-10-04
Duh, thanks....

---

### Post by Dennis Laumen on 2005-10-05
Your welcome, I made that mistake myself once.

It's so basic it will never even cross your mind. ;)

---

### Post by duffydack on 2005-10-05
i especially like the helpful error messages to let you know what to do NOT!!!!

---

### Post by will71110 on 2007-08-18
Anyone know how to make this give permission to other users on  the drive?  Mine wont let me change it from root even if I sudo nautilus.

---

