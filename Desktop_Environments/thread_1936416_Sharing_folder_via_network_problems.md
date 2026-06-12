---
title: "Sharing folder via network problems"
date: 2012-03-06
forum: Desktop Environments
---

### Post by timpire on 2012-03-06
Hi,

I am using Ubuntu 11.04, and i have two main partitions which is 

1. File system - ext3
2. Bk - ext2 (my backup partition)

The problem is when i try to share a folder(name D13) at my Backup partition, it failed.
This is what i have done:
1. mounted partition bk
2. share the folder name D13 (success, with the shared arrow logo showing at the folder icon)
    -guest access (tick)
when i access the D13 share folder from another pc it shows "Unable to mount location. Failed to mount Window share. This situation does not happen to my 1st parttion (File system), sharing via smb works fine for my 1st partition, but for the partition bk, it failed. Is there any extra settings that i've missed up?

Looking forward to any suggestion/help. Thanks

---

### Post by Bucky Ball on 2012-03-06
Under 'System' you don't have 'Samba'? That is the samba server configuration GUI. Make sure bck is in there.

---

### Post by timpire on 2012-03-06
Got it. Thanks. It works now :D

---

### Post by Morbius1 on 2012-03-06
The only possible potential problem you may encounter in the future is:
> 2. share the folder name D13 (success, with the shared arrow logo showing at the folder icon)
    -guest access (tick)From that description you created a **Samba Usershare**. You create them directly from Nautilus. It's share definitions are in /var/lib/samba/usershares.
> Under 'System' you don't have 'Samba'? That is the samba server configuration GUI. Make sure bck is in there.     You just created a **Samba Classic Share**. It's share definitions are in /etc/samba/smb.conf.

Right now it appears as though you created a guest share of the same folder using both methods so it doesn't matter. But in the future should you decide to something different to that share these two methods will no longer be in sync and I don't know who Samba will listen to at that point.

---

