---
title: "Protecting NFS share by its name - is it good or bad idea?"
date: 2006-05-14
forum: Desktop Environments
---

### Post by Martin Pilka on 2006-05-14
Hello all,

recently I learned that NFS does not really support any security model. But what if I put some "password" into share name, i.e.

192.168.1.2:/nfs_shares/secret_share_Xfdg4gDTh

I am not aware of utility which shows names of NFS shares, is there such? (similar to "smbclient -L //192.168.1.1" command in Samba world). If not, this could be a simple way to protect NFS share, even not very secure - I guess NFS names come through network in plain text...

Martin

---

### Post by Martin Pilka on 2006-05-22
Not a way, "showmount -e" shows NFS exports.
Martin

---

