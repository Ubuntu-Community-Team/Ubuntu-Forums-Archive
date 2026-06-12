---
title: "simple permission question"
date: 2009-03-09
forum: General Help
---

### Post by Carlsl on 2009-03-09
Hi, I have a simple permission question. I understand that there are read, write and execute permissions for user, which is the owner, and group, and other. 

    my question is what's the purpose of  owner permission. I mean owner has all permission, so it does not make sense to enable owner to his own permission. 

Thanks,

---

### Post by aMadMan on 2009-03-09
the point of it is efficiency and flexibility.

if i create the file then i am the owner, i may want certain groups or other users to be able to read, write or be able to execute it or i may want to ban any or all of those as well.

one scenario where i the owner would want to tinker with my own permissions would be in the case where i want to make a file read only, so that even i myself can't accidentally overwrite it.

linux was originally aimed towards a server environment, so if your are strictly using it as a desktop, some of the permission stuff mite not seem as usefull unless you have lots of files you want to protect.

google "linux file permissions" and just start reading up about it.

---

