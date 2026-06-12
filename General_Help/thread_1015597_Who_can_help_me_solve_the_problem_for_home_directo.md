---
title: "Who can help me solve the problem for home directory?"
date: 2008-12-19
forum: General Help
---

### Post by jiangyue9674 on 2008-12-19
Hi,guys.I'm just trying to use pam_mount with ldap and samba to get a map for home directory.I'm working on the client side, and wanna map user's home folder to the one on the server.But my configuration does not work and I do not know where the problem is and how to solve it, so any suggestions much appreciated.

This is my common-auth file:
auth    sufficient    pam_unix.so nullok try_first_pass
auth    required       pam_ldap.so use_first_pass
auth	optional	pam_smbpass.so migrate
auth     required      pam_mount.so use_first_pass

This is my common-session file:
session                 sufficient      pam_unix.so
session                 required        pam_ldap.so
session                 required	pam_mkhomedir.so skel=/etc/skel/
session    		optional        pam_mount.so use_first_pass

This is the part i changed in pam_mount.conf.xml file
<volume user="*" fstype="smbfs" server="magpie" path="/homes/%(USER)" mountpoint="/home/%(USER)" />

---

### Post by reality1011 on 2008-12-19
I think you need to better explain  the situation better...  It sounds like you are trying to use a windows formatted partition (NTFS) to mount as your home directory?  If so I dont know if that is possible since windows and unix have 2 different file systems.  I wouldn't take this last thought as being true, I have never worked with samba.

Are you having any error messages in the console or system logs?

Have you looked into NFS ?  This past week I just created a networked home drive, which is automounted in 2 computers and they both share it, so I am able to use the same home directory and my scripts, etc are shared in both boxes...  It sounds like something you are trying to do...

---

### Post by jiangyue9674 on 2008-12-20
Thanks for reply.

My situtaion is that the server is runing with Windows Server Edition, and I am working on two client hosts, The thing I wanna do is that I need create a folder for each user when they logining on these two client hosts I'm working on, the folder is mounted with the corresponding folder on the server.

Now I'm used samba already, and i am trying to use pam_mount to automatically mount when login(auto unmount when login out as well).So any more suggestions?

---

