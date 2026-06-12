---
title: "How to create a web directory along with a user account??"
date: 2006-10-07
forum: Desktop Environments
---

### Post by sands on 2006-10-07
I installed apache..
When creating a new user, I want a web directory also to be created for him.. Something like, when we register for a webhosting service, we get our own directory. And I also like to know how to access that user web directory. I want a subdomain name like sands.sands.com, if the user name is sands.. How to all this??

---

### Post by kidders on 2006-10-07
Hi there,

I imagine you could put files you want added to new users' homes into /etc/skel. You could perhaps make a little script to create the corresponding subdomain for you.

---

