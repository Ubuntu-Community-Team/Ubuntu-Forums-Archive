---
title: "samba file server: setting user permission (umask)"
date: 2009-01-22
forum: General Help
---

### Post by pavallokazzo on 2009-01-22
Hi there.
I'm switching from Debian to Ubuntu Server 8.04 LTS on a file server we are using at office
I'm stopped while configuring samba (:):))...!
Here some infos:
I have a bunch of USER on the server plus a PRIVATE and a PUBLIC user, all with their nix account and a HOME folder.
USER(s) use their /home/$USER for private files and /home/private folder for office file sharing, while /home/public is kept for files and services available also to guest users.
I did copied USER(s), PRIVATE and PUBLIC account also in samba (smbpasswd USER, password set to the same as nix account)...
Also, USER(s) accounts are part of the PRIVATE group, and looking through the old /etc/passwd revealed that PRIVATE was actually their primary group...

I managed to have dir/file creation to $USER:$USER u+rw in /home/$USER and $USER: private ug+rw in /home/private, while every connection to /home/public are mapped to public:users and permissions are set to ug+rw (0022, default umask).
But I did forgot how!

My smb.conf has:
[home]
...
create mask = 0700
directory mask = 0700

[private]
...
create mask = 0770
directory mask = 0770

[public]
...
force user = public
force group = users
guest ok = yes


Anyone please can come out and help me to get back the old configuration? I backup'd up the debian installation anyway so if you want I can post you some data at request...

---

### Post by pavallokazzo on 2009-01-22
I'm experiencing strange problems now...
If I try to connect a windows user with net command I can connect to Home folder but connecting to:
- PRIVATE folder gives system error 5
- PUBLIC folder gives system error 2221

When I do smbtree, if it works, I get some "timeout connecting to 195.210.87.131:445 (or 139)" and this is not an ip from our lan plus "Error connecting to 195.210.87.131 (operation already in progress)
cli_start_connection: failed to connect to $NETBIOS-NAME<20> (195.210.87.131). Error NT_STATUS_ACCESS_DENIED" and this is replied to all the computers in the network.... wth is this???

---

