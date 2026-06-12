---
title: "Add pc to windows domain"
date: 2009-06-15
forum: General Help
---

### Post by glennbtn on 2009-06-15
Hi
 
I am trying to get Ubuntu workstation on to a windows domain as such using **Likewise. **When I try to get it on to the domain it says it can't find servername.local even thought the network dns is setup to point to the server for web access. I also get an error say about making sure that its setup to use dns in the nsswitch (don't understand this bit)
 
Any advise would be great as very new to this
 
thanks

---

### Post by Amilo1718 on 2009-06-15
i'd try samba ;)

---

### Post by ZackM on 2009-06-15
I can help you with this! Haha. Here's a link to a little tutorial that really helped me:

[https://help.ubuntu.com/8.10/serverguide/C/likewise-open.html](https://help.ubuntu.com/8.10/serverguide/C/likewise-open.html)

It's pretty easy to do with that as a reference. After you get likewise, joining the domain is pretty easy.

sudo domainjoin-cli join dns/ip adminuser

It'll prompt you for a password with:

adminuser@dns/ip:

Then you should get a "SUCCESS" after that, letting you know that you have joined the domain.

Now, after that you want to put in a line in the lwiauthd.conf the path being: /etc/samba/lwiauthd.conf That line will enable you to login directly to the network without having to had WORKGROUP/Login everytime you get on.  Also add that code to the smb.conf (/etc/samba/smb.conf) and you should be all set. Restart, and try logging in with a domain login.

---

### Post by munky99999 on 2009-06-15
> **Amilo1718 said:**
> i'd try samba ;)
samba the working and such version doesnt do active directory all that well. Sure you can integrate and such but it's poor.

Samba4 which is in the repositories is an alpha version that is supposed to do a much better job.

Though if you simply want to be sharing login details and all that. The linked page should work the job.

---

### Post by glennbtn on 2009-06-15
Thanks all and I will give that a go ZachM, many thanks

---

### Post by ZackM on 2009-06-15
Anytime. If you run into any problems don't hesitate to ask for help again. Some of this stuff can be tricky. Haha. Good luck!

---

### Post by glennbtn on 2009-06-17
Ok So tried this and it still don't work. The server name is server1.domainname.local, I can ping server1 no problem but when I add to the domain I still get the dns error or nsswitch advisory. The laptop is called linux-pc and when I try to do anything in terminal it does say it can't locate linux-pc, don't know if this has anything to do with it.
 
Thanks

---

