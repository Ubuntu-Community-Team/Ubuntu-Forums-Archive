---
title: "Unable to mount smb shares with cifs"
date: 2005-12-10
forum: Desktop Environments
---

### Post by giftnudel on 2005-12-10
This was not really a problem, I forgot to give that user access in smb.conf on the server ...

OBSOLETE:

Hi,
i'm running Breezy on a laptop and want to have access to the shares on my server (192.168.0.1). 
The server is running Fedora Core 2 with samba-3.0.10 and I can access all the shares correctly from Win2000. I can also mount the shares on the server with ```
SERVER$ mount -t cifs //192.168.0.1/daten /some/mount/point -o user=user
``` so it actually works.

However, I can't mount it from the laptop using the following command:```
LAPTOP$ mount -t cifs //192.168.0.1/daten /some/mount/point -o user=user
Password:
mount error 13 = Permission denied
```
Anyhow, since it doesn't work and I don't get any useful error messages, neither on the laptop nor on the server, I need some help or some ideas on what I can try.

giftnudel

P.S.: The server shows
```

Dec 10 18:36:30 SERVER samba(pam_unix)[9321]: session opened for user user by (uid=0)
Dec 10 18:36:30 SERVER samba(pam_unix)[9321]: session closed for user user
``` so I get a connection, but I don't know where it fails.

---

