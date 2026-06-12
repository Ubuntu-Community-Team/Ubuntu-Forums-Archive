---
title: "Ubuntu in the office"
date: 2008-10-16
forum: Desktop Environments
---

### Post by Jay_Rock on 2008-10-16
I like Ubuntu it was one of the first distro's I started with. 
Fedora 7 was used for hands one and studying for earning the Linux+. Coming form a Windows world it was hard. Studied and prepared hard then failed. Studied harder-then pasted.

My question is for someone like me that wants to deploy Ubuntu 8.10 to an office of 10-15 office professionals how do I control their desktops from a centralized location. 
Windows uses Active Directory for user accounts and whatnot. 
SUSE has zenworks and other tools to manage computers on your LAN. 
I haven't heard how Ubuntu manages this. 
Last month I started looking at SUSE because of this issue. 
Help.

---

### Post by penguinpi.com on 2008-10-16
LDAP!!!

it's great

[http://www.openldap.org/](http://www.openldap.org/)

~# apt-get install slapd

---

### Post by Jay_Rock on 2008-10-27
Is LDAP going to allow me to due to following: 
Control the end user desktop. 
Have some type of group policy "like" control other computers? 

BTW: NFS is much faster then Window Networking regarding moving large file-I've found.

---

### Post by skullmunky on 2008-10-27
I'm interested in this too - what kind of control do you need?  authentication and central file server; remote admin; automated batch admin; etc?

I use NIS and NFS for a similar-scale environment, but just for user and account control, nothing else fancy...

---

