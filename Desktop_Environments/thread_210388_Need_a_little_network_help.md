---
title: "Need a little network help"
date: 2006-07-06
forum: Desktop Environments
---

### Post by someusernoob on 2006-07-06
Im a little lost in the network configuration...

The situation:

PC1

/media/Data/Network/ = shared with samba (ext3 disk)

```

[Network]
path = /media/Data/Network
available = yes
browseable = yes
public = yes
writable = yes

```

PC2

/home/mom/Netwerk = shared with samba

```

[Network]
path = /home/mom/Netwerk
available = yes
browseable = yes
public = yes
writable = yes

```

I can browse both folders from both computers. But i do not have write permissions.

So the thing i did was changing permissions to the folder on PC2 from (mom:mom) drwxr-xr-x to (mom:mom) drwxrwxrwx.

Now i can actually write from PC1 to the folder in PC2, but then i do not have permissions on the file on PC2 (permission= (nobody:nogroup) drwxr-xr-x) .  So i can not delete the file from the folder. (Its possible with sudo rm *file, but thats not how its supposed to be.)

And now my question is very simple, what is the best way to get normal write permission?

---

### Post by nashjc on 2006-07-06
writEable ??

I don't know if that is the problem, but I do know my scripts have 
writeable = yes

JN

---

### Post by someusernoob on 2006-07-07
No, it shows writable everywhere, also in the commented sections of /etc/samba/smb.conf

Anyway, i started again this morning, and found my way back in that config file. 

With a little help from [this]("http://ubuntuguide.org/wiki/Dapper#How_to_share_public_folders_with_read.2Fwrite_permissions_.28Authentication.3DNo.29") guide i got it configured the way i want now. Only thing i did was changing  /home/public to the directories i showed in my first post.

---

