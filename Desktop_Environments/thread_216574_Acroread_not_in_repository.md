---
title: "Acroread not in repository"
date: 2006-07-15
forum: Desktop Environments
---

### Post by manwe on 2006-07-15
Hi all, 
I've performed a barebones dapper install, I've also enabled the universe and multiverse repositories, updated and upgraded apt-get, but acroread isn't found using synaptic nor through apt-get install acroread. Error: package acroread not found. Any ideas on the issue s? Thanks

---

### Post by carontis on 2006-07-15
In Ubuntu: Application ==> Add/Remove ==> select Show non supported applications and in there you'll find it. 
If you can't see the Add/Remove in your Menu, is 'cause isn't enabled; so: Applications ==> Tools ==> Alacarte and check for Add/Remove and select it. After this go back to the first told part. 

bye

---

### Post by manwe on 2006-07-15
I guess I should have mentioned earlier but my install is very barebones. I have only installed the basic x-windows programs,  firefox, synaptic, and I'm running fluxbox as my windows manager. How do I enable 'show non-supported applications' from the terminal?

---

### Post by Jagot on 2006-07-15
You need to enable the multiverse repo which can be done within Synaptic - see here:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

When it talks about going to "System" > "Administration" > "Software Properties" instead you can open Synaptic and go to "Settings" > "Repositories" then follow the rest.

Alternatively you can do this the manual way:

[http://psychocats.net/ubuntu/sources.php](http://psychocats.net/ubuntu/sources.php)

---

