---
title: "NFS or Samba when sharing between linux?"
date: 2005-06-15
forum: Desktop Environments
---

### Post by GoldBuggie on 2005-06-15
Hi

I got a small home network. 1 stationary computer and 1 laptop connected thrue a hub. I got 2 HD's on the stationary computer and I want to share the HD were linux isn't installed. I managed to share the HD to the network(rightclick on the folder->share etc (together with some manual smb.conf edit)). But whatever I do in smb.conf "writable = yes or read only = no" I can't get the HD to be writable. (The HD is fat32 btw) 

After weeks of trying to look thrue how to's searching the nice ubuntu forum and trying things I still can't get samba sharing to work when I want the HD to be writable. So if you have any help in this area please do tell.

Today I started to think in NFS terms but on thing that I never see stated anywere is wheter the server must be online everytime the client boots. Can I start my laptop then boot my stationary computer and then the mounting business will take care of it self? Getting it to work when both computers are online seems to be a breeze. Anyone that knows the answer?

It seems to be written that NFS is faster but it doesn't seem to be flexible in the sence that was mentioned above.

Help in this matter would be appreciated. It is a drag not to get a shared writable HD.

Here is a part of smb.conf(so much other stuff that is preconfigured that seems unrelevant)

> workgroup = MUHAHAH
guest ok = yes
security = share

[MANIAC]
path = /mnt/hdb/
read only = no
writable = yes
force user = JOE
force group = users
case sensitive = no
msdfs proxy = no
create mask = 0777
directory mask = 0777

Thank you for your time

---

### Post by sonny on 2005-06-15
I had the same problem (linux--xp), the way I solved it was creating samba users and changing the security to user, then add the users to the smb.conf file for each folder. I've heard that networks linux---linux should use nfs, but once I had a friend comming to my house with his linux laptop, I created an account for him, and we didn't had problems at all. May be is not the neatiest way to run a linux network but if it works you don't have to change it.

---

### Post by wylfing on 2005-06-16
I would really recommend going with NFS. Samba is a great tool for sharing resources with Windows boxen but it's very finicky (as you are experiencing) and purely unnecessary when no Windows boxen are present.

To answer your NFS availability question: NFS is very robust. If the NFS shares aren't available, you'll just see an empty directory where the NFS mount point is. No big deal. In practice I've found NFS connections still perfectly functioning after forgetting them for weeks, surviving fine across reboots.

I've experimented with both the kernel-level NFS and userland NFS and I recommend the userland version. It's much more tolerant.

---

