---
title: "Can't access smb share on another server"
date: 2006-06-02
forum: Desktop Environments
---

### Post by thaddeusq on 2006-06-02
I just upgraded from breezy to dapper and now I can't connect to a smb share on another server that I could before upgrading. I attempt to connect by clicking on Places>Connect to Server I've tried choosing Windows share and custom. 
The error that I get is:
"smb://192.168.1.14/P-Drive" is not a valid location.
Please check the spelling and try again.

When I run:
```
smbclient -L 192.168.1.14
```

I get:
```
thaddeus:~$ smbclient -L 192.168.1.14
Password:
Domain=[PIKACHU] OS=[Unix] Server=[Samba 3.0.7-2.RH9]

        Sharename       Type      Comment
        ---------       ----      -------
        P-Drive         Disk      Publicly accessable documents and files
        Accounting      Disk      Accounting's shared folder
        HR              Disk      Human Resource's
        IT              Disk      IT Dept.
```

Any ideas how I can get this to work?
Thanks.
Thad

---

