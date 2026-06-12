---
title: "User account question"
date: 2009-04-20
forum: General Help
---

### Post by DanglyParts on 2009-04-20
I recently was working at chrooting users for a secure ftp server.  Since I have slid that to the wayside, I have an issue with the user accounts and I cannot find the notes of what I did, or remember where I got the instructions.

Basically, I have a user who cannot ssh into my server, because his user account is locking him to sftp only.

His user account window is: 
Home Directory:  /home/user/./
shell:  /bin/sftpsh

Even if I delete his account and remake it, it defaults to these settings.  And I have no notes on what I did.

I'll appreciate any help.

---

### Post by Iowan on 2009-04-20
You *might* edit the shell definition in /etc/passwd.

---

