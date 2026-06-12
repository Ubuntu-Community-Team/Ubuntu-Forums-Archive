---
title: "Ubuntu and admin rights for active directory users"
date: 2009-06-09
forum: Desktop Environments
---

### Post by nublaii on 2009-06-09
We are planning on moving to ubuntu a bunch of our computers.

Using likewise5 we were able to join the computers to the windows server 2003 domain with no problems.

We wanted to give admin rights to the IT users (they belong to the 'tech' group inside the domain), so we accomplished that by adding the line 

```
%DOMAIN\\tech ALL=(ALL) ALL
```

to the sudoers file.

But apparently gnome doesn't pull all the admin rights from that file. For some specific tasks, like access to the 'Users and groups' tool from the admin menu, seems like you need to belong to the admin group.

So the question is, is there an easy way of adding the group 'DOMAIN\tech' to the 'admin' group in ubuntu? what would be the best way to do this?

---

