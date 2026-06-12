---
title: "Samba permission problem driving me nuts"
date: 2009-06-21
forum: General Help
---

### Post by japher on 2009-06-21
I'm having a problem with the samba shares shares that are available on my NAS. From my laptop running Ubuntu 9.04 I can connect to the shares, browse the files, read and write etc. However if I create a file or directory, I cannot read or write that file (only delete it).

Here's my smb.conf from the NAS (the share's I'm interested in are SHARE and SHARE2):
```

[global]
config file=/etc/samba/smb.conf
unix charset = CP437
dos charset = CP437
os level = 8
workgroup = workgroup
server string =
printcap name = /etc/printcap
load printers = no
max log size = 10
security = user
encrypt passwords = yes
smb passwd file = /etc/samba/smbpasswd
socket options = TCP_NODELAY SO_KEEPALIVE SO_SNDBUF=16384 SO_RCVBUF=16384
preferred master = yes
dns proxy = no
preserve case = yes
short preserve case = yes
default case = upper
case sensitive = no
mangled names = yes
null passwords = yes
dos filetimes = yes
veto files = /.ShareConfFile/quota.user/quota.user~/lost+found/$*/System Volume Information/
delete veto files = False
force directory mode=771
force create mode=660
create mask=771
map system=yes
map to guest=Bad User
guest account=guest
name resolve order = wins bcast
include = /etc/samba/user_smb.conf
[ADMIN 2]
valid users=@"administrators"
comment=
path=/share/flash/data/
read only=yes
write list=@"administrators"
[DISK 2]
valid users=@"administrators",@"everyone"
comment=For everyone
path=/share/flash/data/public/
read only=yes
write list=@"administrators",@"everyone"

[SHARE]
valid users=@"administrators",@"everyone"
comment=For everyone
path=/mnt/share/
read only=yes
write list=@"administrators",@"everyone"

[SHARE2]
valid users=@"administrators",@"everyone"
comment=For everyone
path=/mnt/share2/
read only=yes
write list=@"administrators",@"everyone"

```On the laptop running Ubuntu, I've added two lines to */etc/fstab* like:
```

//slug/share      /media/share      cifs    guest,rw,file_mode=0777,dir_mode=0777    0    0
//slug/share2    /media/share2    cifs    guest,rw,file_mode=0777,dir_mode=0777    0    0

```Now, when I attempt to create a file on the share, here is the output:
```

/media/share2$ touch test.txt
touch: setting times of `test.txt': Permission denied
/media/share2$ ls
-rw-rw----  1 501 501 0 2009-06-21 17:06 test.txt
/media/share2$ rm test.txt 
rm: remove write-protected regular empty file `test.txt'? y
/media/share2$

```Anyone have any ideas? I've checked my NAS, and user 501 *is *the guest user. I guess there's a problem here with the owner of the created file being 'guest' and the default permissions for a created file not allowing others to see the file. But if I'm logged on to the share as guest (must be, since guest is the owner of files I create), then why can I not read/write to these newly created files?! It's as if I *am* guest where file creation is concerned, but I am *not *guest where file access is concerned.

:confused:

---

### Post by blueridgedog on 2009-06-21
Since you are mapping the shares as a guest (not a good idea, but lets roll with it) Have you tried adding:

```
guest ok = yes
```

To each share and removing the map to guest=Bad User directive in the global config?

What is in the samba error log?

---

