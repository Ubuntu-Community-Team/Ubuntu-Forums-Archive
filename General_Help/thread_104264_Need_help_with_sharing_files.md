---
title: "Need help with sharing files"
date: 2005-12-15
forum: General Help
---

### Post by cooldudejz on 2005-12-15
ok so i have a computer running ubuntu and a computer xandros, how do i share files betwee the two. they are both hooked up to the same network. how do i config samba to do this. i tried to do it but it didnt work. need help. thanx

---

### Post by cooldudejz on 2005-12-15
bump

---

### Post by soulestream on 2005-12-15
if they combined all the file sharing threads together it would wrap around the world at least 200 times. 

search the forum. search google.

if you are just using linux to linux you dont want samba, you want NFS. google "NFS howto"

if you have a mixed network (windows and linux) then you need samba. if you need that just go up to search and type in samba. it gets explained by the many helpful people here about 5 times a day.


soule

---

### Post by wylfing on 2005-12-15
Well, a lot of people don't know about NFS, because they're accustomed to having to share networks with Windows boxen.

The first thing you need to do is get the NFS server and client software installed on both computers. The Ubuntu packages you need are nfs-common and nfs-kernel-server. Install them with Synaptic. I don't know what the Xandros packages are, but since Xandros is Debian-based it should be something similar.

Now try this: Open a Nautilus window and right-click on a folder you want to share, and choose Share folder. Choose NFS from the drop-down list. Click Add Hosts and select who is allowed to access the shared folder. That's about it!

I think from the Xandros side you can browse for NFS shares pretty easily, but I don't believe Ubuntu can do that. But you don't really want to have these things mounted via VFS anyway -- just mount them "for real" and use them as part of your local file system. See here:
[http://tldp.org/HOWTO/NFS-HOWTO/client.html](http://tldp.org/HOWTO/NFS-HOWTO/client.html)

---

