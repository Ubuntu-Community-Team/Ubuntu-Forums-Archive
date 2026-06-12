---
title: "Trouble mounting samba share"
date: 2009-06-17
forum: General Help
---

### Post by tg1 on 2009-06-17
Hi!

I'm struggling a bit with mounting a samba share (which has worked before)..

When trying to mount the share (locally, on the same box that the share is), I get this message:
```
root@sandman:~# smbmount //192.168.1.10/filserver /mnt/filserver/ -o noperm
Password:
mount error 5 = Input/output error
```

When trying smbclient, I get this:
```

root@sandman:~# smbclient //192.168.1.10/filserver -N
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.2.3]
Server not using user level security and no password supplied.
smb: \> ls
NT_STATUS_NETWORK_ACCESS_DENIED listing \*

                0 blocks of size 0. 61680 blocks available

```


I get this message in /var/log/syslog:
```
Jun 17 11:12:56 sandman kernel: [40921.726855]  CIFS VFS: Send error in QFSAttributeInfo = -5
Jun 17 11:12:56 sandman kernel: [40921.727009]  CIFS VFS: Send error in QFSUnixInfo = -5
Jun 17 11:12:56 sandman kernel: [40921.727164]  CIFS VFS: cifs_read_super: get root inode failed
```

Also worth mentioning is that there is no password authentication on the share ("security = share" in smb.conf).

I'm not very familiar with troubleshooting samba, so any help will be appreciated. :-)

---

### Post by kixome on 2009-06-17
have you tried mounting it through nautilus?

---

### Post by kixome on 2009-06-17
typically I go to Panel>places>network>windows network>hostname

 I hope this helps. I am no expert just an intermediate user.

---

### Post by tg1 on 2009-06-17
When I enter smb://192.168.1.10 in nautilus, it lists the correct folder, but when I try to enter this folder, i get "Unable to mount location".

---

### Post by Xanthomryr on 2009-06-17
Please show us your /etc/samba/smb.conf.

---

### Post by tg1 on 2009-06-17
Here goes:
(removed all commented lines)

```

[global]
   workgroup = WORKGROUP
   server string = %h server
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   security = share
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   invalid users = root
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
   socket options = TCP_NODELAY
   wins support = no

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   public = no
   writable = no
   create mode = 0700

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

[filserver]
  comment = Filserver
  path = /array/
  public = yes
  writable = yes
  create mask = 0777
  directory mask = 0777
  force user = nobody
  force group = nogroup

```

---

### Post by tg1 on 2009-06-18
Anyone? :-)

Edit: problem solved. Turned out to be a premission problem on the directory i tried to mount... :oops: :-\"

---

