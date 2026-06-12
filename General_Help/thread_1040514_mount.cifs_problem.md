---
title: "mount.cifs problem"
date: 2009-01-15
forum: General Help
---

### Post by uvdevnull on 2009-01-15
I'm having a problem using an external credentials file for mount.cifs

When I have the options listed in fstab, mounting works fine:
```
//server1/share1 /media/samba/share1 cifs user=user1,pass=password1,dom=mydomain,noexec 0 0
```
However, when I specify an external credentials file, it fails:
```
//server1/share1 /media/samba/share1 cifs cred=/etc/samba/cred1,noexec 0 0

``````

[app04: /media/samba]$ sudo mount /media/samba/share1
Password:
mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
```
Contents of cred1:
```
user=user1
pass=password1
dom=mydomain
```
Mounting in verbose shows that the credentials file is not properly parsed:
```

[app04: /media/samba]$ sudo mount --verbose /media/samba/share1
parsing options: rw,noexec,cred=/etc/samba/cred1
Password:
(typing "typedpassword")
mount.cifs kernel mount options unc=//server1\share1,ip=192.168.1.69,user=root,pass=typedpassword,ver=1,rw,noexec,cred=/etc/samba/cred1
mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

```

---

### Post by uvdevnull on 2009-01-15
Solved by changing the variable names in the credentials file to the smbfs style.  The man page for mount.cifs says you can use them interchangeably but apparently only via the command line or fstab, not in the external credentials file.  Should have read the second page of the manual :)
```

username=user1
password=password1
domain=mydomain
```

---

