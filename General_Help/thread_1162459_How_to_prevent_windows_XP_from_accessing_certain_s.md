---
title: "How to prevent windows XP from accessing certain shares"
date: 2009-05-17
forum: General Help
---

### Post by charlebp on 2009-05-17
Hello,

New to Linux and am having some trouble with samba.

Everything is installed and appears to be working.  From my XP Machine I can connect to the shares I have setup.  Problem is that I am setting this up for our office as a small file server and want to restrict users from accessing certain shares.  I have user A and user B, one folder shared as general and another as finance.  I am trying to set it up such that when user B goes to \\server from windows xp box she cannot see the finance share.  I have created Linux users and samba users, I have also added to smb.conf the following:
[finance]
path = /some/folder
valid users = A
browseable = no

Any suggestions would be appreciated.

Thanks

Phil

---

