---
title: "Samba shares"
date: 2006-10-05
forum: Desktop Environments
---

### Post by utab on 2006-10-05
Dear all,

I am seeking a way to automatically mount network folders when I log in. I put the related entries into /etc/fstab

but at every log in I have to run

sudo mount -a

the related lines for the pool in fstab are:

//filesrv/pool /home/utab/documents/MECH_POOL smbfs username=....,password=.......,dmask=777,fmask=777 0 0

and

//10.33.175.17/utabak /home/utab/documents/MECH_HOME smbfs username=.....,password=........,dmask=777,fmask=7 77 0 0

regards,

---

### Post by Iowan on 2006-10-05
[http://justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html]("http://justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html")
This help?

---

