---
title: "Permission problem"
date: 2008-12-08
forum: General Help
---

### Post by NickDeGraeve on 2008-12-08
I have a directory that is owned by user 'ps' and group 'libvirtd' and with permission 775.```
ndg@SVR-DEV:~$ ls -la /opt/vm/
total 102028
drwxrwxr-x 2 ps   libvirtd      4096 2008-12-08 08:58 .
drwxr-xr-x 6 root root          4096 2008-12-08 08:58 ..
```
My user, 'ndg', is also a member of the 'libvirtd' group:```
ndg@SVR-DEV:~$ cat /etc/group | grep libvirtd
libvirtd:x:124:ndg,ps
```However I can't write to the directory:```
ndg@SVR-DEV:~$ touch /opt/vm/something
touch: cannot touch `/opt/vm/something': Permission denied
```
There's something strange going on because when I run 'id' the 'libvirtd' group isn't listed:```
ndg@SVR-DEV:~$ id
uid=1000(ndg) gid=1000(ndg) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),107(fuse),111(lpadmin),112(admin),115(sambashare),1000(ndg)
``` but when I run 'id ndg' it is!```
ndg@SVR-DEV:~$ id ndg
uid=1000(ndg) gid=1000(ndg) groups=1000(ndg),4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),107(fuse),111(lpadmin),112(admin),115(sambashare),124(libvirtd)
```And trying to 'ndg' to the 'libvirtd' group also states that it is a member:```
ndg@SVR-DEV:~$ sudo adduser ndg libvirtd
[sudo] password for ndg:
The user `ndg' is already a member of `libvirtd'.
```

So why can't I write to the directory?

---

### Post by NickDeGraeve on 2008-12-08
Logging out and back in again fixed it. I didn't know about this behavior. You learn something every day. :-)

---

