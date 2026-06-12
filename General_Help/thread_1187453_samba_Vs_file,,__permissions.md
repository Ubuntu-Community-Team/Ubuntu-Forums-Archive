---
title: "samba Vs file,,  permissions"
date: 2009-06-14
forum: General Help
---

### Post by tatt on 2009-06-14
I am setting up a SAMBA file server with various permissions for access.
I am adding the users and groups using addusr etc.

Will SAMBA therefore handle the file access permissions if i am using the lines in smb.conf........... "valid users = *** *** ***" and  "write list = *** *** ***".

Basically, what im asking is.....

Can I leave alone the ubuntu file permissions i.e as my user name as owner with "create and delete" and my users group as "create and delete"......will SAMBA overule this when a different user logs in through SAMBA or will i have to set the "others" as "create and delete" also. 

Thanks.

Chris

---

### Post by mhgsys on 2009-06-14
samba will use the options given by you in the smb.conf

Therefore, 
If you allow other user to create and delete files in samba, you won't have to adjust other settings in your user account.

Hopes that answers your question.

---

### Post by tatt on 2009-06-14
Thanks for your time.

Chris

---

