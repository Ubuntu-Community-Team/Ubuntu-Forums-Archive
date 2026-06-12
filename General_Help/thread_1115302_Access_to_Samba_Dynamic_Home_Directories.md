---
title: "Access to Samba Dynamic Home Directories"
date: 2009-04-03
forum: General Help
---

### Post by Fynn on 2009-04-03
I have a Samba Server with dynamic home drives.

[homes]
  comment = Home Directories
  read only = no
  browseable = no
  valid users = %S
  writable = yes
  path = /home/%U
  inherit permissions = yes

Is there a way of adding myself to the list of people that can connect to these shares?  I tried adding my own userid to the list of valid users, which gave me the correct share name but linked through to my own home drive.

---

### Post by kanikilu on 2009-04-03
> **Fynn said:**
> I have a Samba Server with dynamic home drives.

[homes]
  comment = Home Directories
  read only = no
  browseable = no
  valid users = %S
  writable = yes
  path = /home/%U
  inherit permissions = yes

Is there a way of adding myself to the list of people that can connect to these shares?  I tried adding my own userid to the list of valid users, which gave me the correct share name but linked through to my own home drive.

I haven't setup Samba to share home directories yet, but I think the **path = /home/%U** is what's directing you to your home directory instead of the other user. I'm not really sure how to get around this, though, sorry...

I'm curious why you'd want to mount another user's home directory, though...

Couldn't you maybe create a new share to one directory up (/home) and give just yourself permission to it, and then you could mount that and then just browse into the sub-directories?

---

### Post by Fynn on 2009-04-03
> **kanikilu said:**
> 
I'm curious why you'd want to mount another user's home directory, though...


It's just a home server, and sometimes the kids end up saving work on my desktop which I need to dump back into their home directories.

> 
Couldn't you maybe create a new share to one directory up (/home) and give just yourself permission to it, and then you could mount that and then just browse into the sub-directories?

That's the perfect solution, and it was staring me right in the face!  

Thanks

---

