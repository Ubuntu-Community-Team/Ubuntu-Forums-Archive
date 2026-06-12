---
title: "LikeWise domain user rights"
date: 2009-06-02
forum: General Help
---

### Post by kirilloff on 2009-06-02
Hi everyone.
I installed LikeWise, and Likewise GUI packages
succesfully joined windows AD domain
i also can login at startup (in GDM) using domain user name (for example) DOMAIN.COM\\duser

The problem i have is following:
i can't edit rights and permission level of this duser, course i have no such user in my system 
i only have a folder named DOMAIN\duser in /home

So my question is - 
how can i edit rights of duser?

Thanks in advance.
Sorry for my english.

---

### Post by Stuart42 on 2009-06-03
You need to edit /etc/group to give it some rights. I've added 'DOMAIN\username' to groups my admin user was in before, and I've also added this to my sudoers file using visudo

DOMAIN\\username ALL=(ALL) ALL

Or you can give it to groups like this:
%DOMAIN\\domaingroup ALL=(ALL) ALL

Just keep in mind to use the appropriate escape characters. 'DOMAIN\Group Name' will work, or DOMAIN\\Group^Name will also work.

---

### Post by kirilloff on 2009-06-04
thanks - i'll try this

---

### Post by kirilloff on 2009-06-08
> **Stuart42 said:**
> You need to edit /etc/group to give it some rights. I've added 'DOMAIN\username' to groups my admin user was in before, and I've also added this to my sudoers file using visudo

DOMAIN\\username ALL=(ALL) ALL

Or you can give it to groups like this:
%DOMAIN\\domaingroup ALL=(ALL) ALL

Just keep in mind to use the appropriate escape characters. 'DOMAIN\Group Name' will work, or DOMAIN\\Group^Name will also work.

well  i understoop that - thanks
but i don't want to make this user admin or sudoer
i want him (domain user) to be completely unprivileged 
(well not completely - he should have access to network, but locally he should be unable to do anything - even browse local filesystem)
can i do that? and how?

---

