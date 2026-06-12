---
title: "Joining an Ubuntu machine to a Windows Domain?"
date: 2009-03-01
forum: General Help
---

### Post by cinmachina on 2009-03-01
Hi all,

I'm trying to figure out how to join an Ubuntu machine to a windows domain so that it can be seen in active directory, and force the user to logon with username///password like in a regular windows domain environment.

Does anyone know how to do something like this?

Thanks in advance,

Cinmachina

---

### Post by cinmachina on 2009-03-01
Anyone know?

/bump

---

### Post by DGortze380 on 2009-03-01
It's typically considered bad etiquette to bump before 24 hrs.

And the answer to your question, to the best of my knowledge, no. Linux doesn't play nice with active directory. Linux will set your "domain" base on actual network settings, IP and Netmask. 

You can access windows shares with Samba.

The only option I know of would be to check your addressing and subnets, and make sure they're correct (the old school way of handling "domains").

EDIT: Some other options I'm not familiar with. [http://www.windowsnetworking.com/articles_tutorials/Authenticating-Linux-Active-Directory.html](http://www.windowsnetworking.com/articles_tutorials/Authenticating-Linux-Active-Directory.html)

---

### Post by Dougie187 on 2009-03-01
There are pretty easy ways, just search around.

It involved Kerberos, and Samba. There are also some clients you can use, but I forget what the name is.

Edit:

A Simple google search gave this.
[http://anothersysadmin.wordpress.com/2008/04/06/howto-active-directory-authentication-in-ubuntu-804/](http://anothersysadmin.wordpress.com/2008/04/06/howto-active-directory-authentication-in-ubuntu-804/)

I think the client is called likewise.

---

### Post by cinmachina on 2009-03-01
Sorry for any psychological damage I may have inflicted.

I do appreciate the response, and will look into it tomorrow at work.

Thanks!

---

### Post by cinmachina on 2009-03-02
So I followed all of the steps, and it said I joined the domain successfully. I even show the computer in Active Directory. However, when I restart the machine it doesn’t prompt me for my network credentials. It’s just the local username/password of the machine as if it had never happened.

What am I doing wrong here?

---

### Post by THGIC on 2011-04-29
Have you tried a program that is offered from the Ubuntu Software Center called, "Likewise Open"? 

Likewise Open has a easy-to-use GUI for joining Linux (Ubuntu) boxes to an already existing Windows Domain. Also, it has a handy command line version that you can use, if you like to do it the old school way.

---

