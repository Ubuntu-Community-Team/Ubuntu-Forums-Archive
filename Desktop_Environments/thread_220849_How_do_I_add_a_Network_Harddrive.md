---
title: "How do I add a Network Harddrive"
date: 2006-07-22
forum: Desktop Environments
---

### Post by Emmett on 2006-07-22
](*,) I just bought and installed a Buffalo HD-HG300LAN Link Station. It works with Win XP now but I have not found any information on how to add it to Kubuntu Dapper. 

1) Is there a How To to follow and install it? 
2) Has anyone else added one to their network?

Emmett

---

### Post by Thund3rstruck on 2006-07-22
I haven't used the Buffalo NAS devices but I've used several others. I have always used smbfs or cifs to mount it. 

There are several threads on mounting windows shares (assuming the NAS is using smb and not nfs)

```

$ sudo mkdir /media/nas

```

edit /etc/fstab

```

//NasIPAddress/Share /media/nas cifs uid=linuxuser,credentials=/etc/.cifspw,workgroup=YourDomain,user,rw,0 0

```

mount the device
```

$sudo mount -a

```

---

### Post by Emmett on 2006-07-22
Thund3rstruck Thank you for repling.

Here is what I put in fstab but still will not mount:

//192.168.1.150/share /Shared/Buffalo cifs uid=emmett,credentials=/etc/.cifspw,workgroup=Mshome,user,rw,0 0

This is what I get with mount -a:

emmett@Kubuntu:~$ sudo mount -a
Password:
mount: wrong fs type, bad option, bad superblock on //192.168.1.150/share,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

The only way I can reach it is if I type in [ftp://192.168.1.150](ftp://192.168.1.150)

Do you have any other thoughts? I have looked at other threads but did not solve this. I am relitively new to linux but this I believe is a easy fix if I knew what I was fully doing. 

Emmett

---

