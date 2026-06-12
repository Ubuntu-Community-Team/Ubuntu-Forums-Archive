---
title: "logogn script for Auto mounting windows share script based on user"
date: 2012-12-23
forum: Desktop Environments
---

### Post by kumar007 on 2012-12-23
I have a question.
I want to have my desktop Join our AD domain using likewize. After joining domain I want to create a script that will mount user based windows share automatically, and should create a symlink to /home/%user
For example, 
Share for domain user1 might look like
//192.168.1.2/user1/ and is redirected from /home/user1 (May be symlink)?
Share for domain user2 might look like this
//192.168.1.2/user2/ and is redirected from /home/user2
Ounce the user logs out, it should unmount the folder.
Thanks in advance.

---

### Post by kumar007 on 2012-12-24
No one???
Please help!!!!!!

---

### Post by steeldriver on 2012-12-24
not a script but maybe autofs would do what you want?

[https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)

---

### Post by kumar007 on 2012-12-24
Thanks for your reply.
I would prefer a script, because this will be deployed for many users who are a part of Active Directory.
Please let me know.

---

### Post by LewisTM on 2012-12-24
I don't think it's possible to use a Windows share as a home folder. Linux needs a UNIX type filesystem that supports permissions and symlinks and whatnot. For network shares that means NFS and perhaps SSHFS, not Samba.

Windows supports "roaming profiles" that resemble NFS homes but involves network syncing to and from a local profile, not diskless network homes. Maybe you could write an rsync script at login/logout that does just that.

You might have better luck mounting or symlinking shares to specific subdirectories such as Documents or .mozilla. Those don't make use of special filesystem features.

Cheers!

---

### Post by kumar007 on 2013-01-03
Mounting on other sub-directory should work for me.
I would still need a script to auto mount it based on user credentials.

---

