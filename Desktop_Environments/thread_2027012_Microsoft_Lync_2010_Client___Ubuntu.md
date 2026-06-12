---
title: "Microsoft Lync 2010 Client _ Ubuntu"
date: 2012-07-16
forum: Desktop Environments
---

### Post by tfernandes on 2012-07-16
Hi all,
 
I'm using Ubunto 12.04 LTS on 8 GB USB disk
Works excellent.:D:D:D
 
Need to install Microsoft Lync Client 2010 on it. 
 
Has anyone tried?
 
Please let me know.
 
Regards,
tfernandes
 
:D

---

### Post by Lazra on 2012-07-16
Hello,

Lync is not supported on Ubuntu, however you could use pidgin with sipe plugin as an alternative. I'm doing it at work, and it's working pretty well. Only drawback is that it's not supporting audio or video calls.

One other solution may be to try to run it with wine, but i'm not sure of the results ...

---

### Post by tfernandes on 2012-07-16
> **Lazra said:**
> Hello,

Lync is not supported on Ubuntu, however you could use pidgin with sipe plugin as an alternative. I'm doing it at work, and it's working pretty well. Only drawback is that it's not supporting audio or video calls.

One other solution may be to try to run it with wine, but i'm not sure of the results ...
hi lazra,
 
thanks for the reply. 
 
i'll try with wine and let out the results
 
as you mentioned use pidgin and sipe plugin so these are clients that connet to microsoft lync server? after installation i need to put the lync server's ip / name? 
 
just a bit confused.
 
tfernandes

---

### Post by Lazra on 2012-07-16
Pidgin is a chat client, and there is a plugin for it called "sipe-plugin" that add the possibility for Pidgin to connect as Microsoft Office Communicator / Lync client.

The info needed to connect are the protocol (Office Communicator), the username (email address), your DOMAIN\username and of course your password.

On my company we were using Office Communicator and we migrated to Lync, and it's working perfectly. I did not have to change anything in my setup when we migrated to Lync, so i think it should work for you too.

You'll need to install packages "pidgin" and "pidgin-sipe" if you want to try it.

---

