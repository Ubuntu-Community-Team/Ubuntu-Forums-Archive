---
title: "setting up network with NFS Samba and authentication"
date: 2009-05-27
forum: General Help
---

### Post by zalnn on 2009-05-27
Hi All,

I have moderate experience with Linux. But when it comes to networking and infrastructure I am still a little clueless. I am trying to use this project as learning opportunity. 

All the machines are networked via a Linksys router running DD-WTR. All the servers have static IPs.

I have a few servers setup at home (all headless Debian/Ubuntu-server):
- c1 fileserver(Raid5) 
- c2 printserver(CUPS) + fileserver(RAID1)
- c3 mythbuntu backend/frontend

In addition to those, my wife and I have laptops that run WinXP and Ubuntu respectively.

I am also going to setup another server "c4" which will be another file server. 

Currently I have manually setup a username and password on all the machines. So far we have accessed the files via Samba.

**What I want:**
1. Have some sort of authentication server (probably on c2) so that the NFS uid/gid are the same on all the machines (can tackle WinXP logins later)

2. I want to be able to setup all the home directories on "c2"

3. Setup the servers with NFS and Samba, where the authentication is handled via the Authentication server (same password/username for Linux and Samba login)

4. I would like to know how to setup the network properly. With a domain etc... So that NetBIOS and DNS will work. Currently if I have a server without Samba, WinXP won't find the machine via the hostname... it needs the IP address.

5. Do I need a domain name? Can my domain be "sub.domain.com", as I already have "domain.com" but it is hosted on a 3rd party server (hosting provider).

Thanks in advance

---

