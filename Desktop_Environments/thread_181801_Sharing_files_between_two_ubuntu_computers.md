---
title: "Sharing files between two ubuntu computers?"
date: 2006-05-24
forum: Desktop Environments
---

### Post by chadk on 2006-05-24
Subject says it all.  I have two dapper PC's and want to share some directories.  How can I do this?  SAMBA isn't a problem but I'd rather not use that between two linux boxes if I don't have to?

---

### Post by chadk on 2006-05-24
[QUOTE=chadk]Subject says it all.  I have two dapper PC's and want to share some directories.  How can I do this?  SAMBA isn't a problem but I'd rather not use that between two linux boxes if I don't have to?[/QUOTE]

oh sheesh... SYSTEM, ADMIN, SHARED FOLDERS... :-k

---

### Post by chadk on 2006-05-24
ok, so I never turned on NFS on my main PC when I started sharing folders with SAMBA.  Now I can't figure out how to get NFS as an option so I can share these folders with the other machine.  -- the other machine works fine because I installed NFS and SAMBA just now when I shared the first folder.

---

### Post by Sef on 2006-05-24
We have all missed the easy things at times.

---

### Post by chadk on 2006-05-24
:) Sef.
Still kinda wondering how to access these shared directories from one computer to the other.  Also need to know how to turn on NFS on one of the PC's that I didn't originally select it on (Dapper).

---

### Post by adamkane on 2006-05-24
It's good you chose NFS. SSHFS is not well developed yet.

Choose one PC as the server. If both are servers, then you will not be able to boot one of the PCs.

Server:
```

sudo apt-get install nfs-server

``` 
Client:
```

sudo gedit /etc/fstab

``` 
Add some lines:

server_ip:/server_folder /local_folder nfs noatime,rsize=32768,wsize=32768,bg 0 0
[SIZE=3]
Example
192.168.0.10:/media/docs     /media/docs     nfs     noatime,rsize=32768,wsize=32768,bg 0 0

Be sure to create some folders on the client:
```

sudo mkdir /media/docs
sudo chmod +x /media/docs

``` 
If you want to move files around, you have to use the client to do this.
[/SIZE]

---

### Post by chadk on 2006-05-25
I had to use sudo apt-get install nfs-kernel-server

-- Hmm what if I use DHCP?  I guess there's no good reason to still be using it but I still do.

---

### Post by adamkane on 2006-05-26
There are ways to make some machines static while using DHCP. There are some howtos. Sorry I don't have the info.

---

