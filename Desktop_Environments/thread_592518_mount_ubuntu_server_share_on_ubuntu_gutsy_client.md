---
title: "mount ubuntu server share on ubuntu gutsy client"
date: 2007-10-26
forum: Desktop Environments
---

### Post by psyghotic on 2007-10-26
Hi i have got a ubuntu server where i made a share /media/servarch1
this i want to mount on my gutsy client under /media/ubserv1

so on my client i created a dir in /media called ubserv1

in fstab on client I have the following : 

//ip-server:/media/servarch1 /media/ubserv1 nfs defaults 0 2

On server /etc/exports I have the following :

/media/servarch1 192.168.0.*(rw,no_subtree_check,async)

Ofcourse I first performed this 

On server :
sudo apt-get install nfs-kernel-server nfs-common portmap
When configuring portmap do =not= bind loopback. If you do you can either edit /etc/default/portmap by hand or run:
sudo dpkg-reconfigure portmap
sudo /etc/init.d/portmap restart

On client:
sudo apt-get install portmap nfs-common

After each change in /etc/exports :

sudo /etc/init.d/nfs-kernel-server restart

But after doeing this all I still get the message can't find ip-server, if I try with servername, same error.
When I ping to the ip-server I get reply

Any Idea

---

### Post by britishbulldog on 2007-10-29
Oops! wrong post

---

