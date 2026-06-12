---
title: "Why do I have to enter my password so much?"
date: 2006-02-19
forum: Desktop Environments
---

### Post by dylanknightrogers on 2006-02-19
I have Samba up and running between 2 Ubuntu 5.10 machines freshly installed.  I have not touched any config files, but I have installed the Samba and NFS services as mentioned.

When I go into Network Servers, I can see the two machines but cannot go inside them.  It asks me for a password like 50 times and then quits.

Why do I have to enter my password, which password is it, and is there any way for it to STOP asking me for one?

That would be helpful.  Please help.  I need to transfer a lot of data from my desktop to my laptop.

---

### Post by nanotube on 2006-02-19
well, best way to transfer your files would be to set up an openssh or ftp server on one of the machines, and then just log in to that from your other box, and transfer away. that's what i did to transfer files, cuz it seemed that samba is too much of a pain in the *** to set up. :)

and btw, if you do go that way, package "gftp" provides a very nice gui ftp/sftp interface for file transfer. :)

---

### Post by dylanknightrogers on 2006-02-20
fixed the issue.

go into /etc/samba/smb.conf

find the line

security = user

and replace it with 

security = share


So simple.

---

### Post by rumz on 2006-02-26
which is better user or share?  i think [guessing] that they had security in mind when thinking of user, maybe if you dont care who accesses then use share... 

anyone have any ideas?

---

### Post by pestilence4hr on 2006-02-26
Between 2 ubuntu machines, you would be better off using NFS.  It's simpler.

Oh, and the password for samba has to be set with smbpasswd, they generally aren't synced with /etc/passwd

---

