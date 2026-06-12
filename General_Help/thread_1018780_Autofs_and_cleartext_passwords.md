---
title: "Autofs and cleartext passwords"
date: 2008-12-22
forum: General Help
---

### Post by afrinspray on 2008-12-22
I am mounting a Samba share (in Linux from Windows) using autofs.  Everything works fine, but I'm a little creeped out about having my password available in the clear in the auto.__ file.  I have chown'd it to be readable by root only, but other people have access to the root account.

I do not have the ability to create a user in the Windows environment.

For example,
mountfolder -fstype=smbfs,username=myusername,**password=cleartext**,...

Any suggestions on how I could encrypt this password?

Thanks.

---

