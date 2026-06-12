---
title: "Can not get access to ubuntu server"
date: 2006-05-02
forum: Desktop Environments
---

### Post by jmarchlew on 2006-05-02
I am trying to setup a ubuntu server for my home network to share files and a printer.  I have installed Samba and I can see the server on my WIndows Xp Home server but I can not access it.  I keep getting this error:

\\server is not accessible.  You might not have the permission to use this network resource.  Contact the the administrator of this server to find out it you have access permissions.

The network path was not found.

I have made changes to the smb.conf file changing these parameters:

browseable = yes
create mask = 0775
directory mask = 0775

and security = share

Any ideas?

---

### Post by zappadragon on 2006-05-03
i am having the same problem and when windows prompts for username and password for my share on the Ubuntu box it never will take the username or pass. I have tried everything. It does the same thing if I try going from my Ubuntu box to a Windows box.

please someone help

---

### Post by cgjones on 2006-05-03
Try running testparm on smb.conf. This will check to make sure that smb.conf is formatted correctly. Also, it might help if you posted the output of testparm here.
```

testparm

```

---

