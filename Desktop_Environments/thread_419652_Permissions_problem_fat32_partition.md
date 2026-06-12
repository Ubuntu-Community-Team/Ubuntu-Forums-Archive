---
title: "Permissions problem fat32 partition"
date: 2007-04-23
forum: Desktop Environments
---

### Post by safapombo on 2007-04-23
Hi there!
I need help, i am going nuts here.

I am trying to share a fat32 partition between 8 different users I have on the network. The server is dualboot Windows XP and Ubuntu server edition.
When booted in Windows, everything works, but when booted in Ubuntu.. nothing does.

I installed Samba. I created users in Linux and Samba, giving them passwords.

But, Linux permissions overwrites Samba's, right? So i figure it is a Linux permissions problem.
Now, I cant change the owner for my fat32 partition (for the folder inside it), and i cant make the folder permissions read and write for everybody (with chown from root and not). The main user (jeremy), which is the first one i registered, can read and write everywhere, but no-one else can. 
I even tried to joing another user to that user's group and see if it works, but nothing. 
Also, i cant change the group that can access that folder, the only group that can access it is jeremy and within jeremy only the username called jeremy.

Am i making myself clear? Can anyone help me please?
Thanks!

---

