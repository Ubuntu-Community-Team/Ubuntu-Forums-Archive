---
title: "Connecting nodes on a network"
date: 2009-03-28
forum: General Help
---

### Post by fmw on 2009-03-28
Hello. I'm a brand new Ubuntu 8.1 user. Finished installing and doing all the updates. Everything is perfect except for my Windows network. It is a 6 node network and this one is the only Linux machine. I need it to have access to my NAS for backup. The network installed properly and I can see the Windows workgroup and icons for each of the nodes. When I try to go to one of the nodes it tells me it can't mount it. I'm sure it is some simple thing I've left unnoticed. My old distro worked happily within this same network. Any suggestions would be apprediated.

---

### Post by cariboo on 2009-03-28
Have you set a samba password? open a terminal and type:

```
sudo smbpasswd -L -a <username>
```

then

```
sudo smbpasswd -L -e <username>
```

The first command lets you set a password for your user and the second command enables that user.

Jim

---

