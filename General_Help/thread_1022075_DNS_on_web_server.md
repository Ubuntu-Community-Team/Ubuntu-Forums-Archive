---
title: "DNS on web server?"
date: 2008-12-26
forum: General Help
---

### Post by zoomiest on 2008-12-26
Just reading [a tutorial]("http://www.howtoforge.com/perfect_setup_ubuntu_6.06") on how to set up a webserver on the same system box as a bunch of other servers (mail, DNS, database, ftp, web stats, pop3/imap, etc.)

My Question(s): 
1. **What is the value of including a DNS server on the same box as a webserver?**

... and while I am asking questions... what is the value of including a pop3/imap server on the same box as general mail server?

I recognize that the tutorial tries to pack the box with as many related servers as possible...), but is there some functionality I do not understand?

How would a DNS server (which functions as a map of the Internet, as I understand it, to help with navigation) help a web server, being on the same box (or even in the same network environment)?

---

### Post by albandy on 2008-12-26
Take it as a learning tutorial. Install as less services as you can in a computer exposed to internet.

I prefer to use a virtual machine for each service.

A DNS server in the network environment is usefull when you have to resolve internal and external addresses.

For example, you've the domain mydomain.com and you've a web server and a mail server.

Internally when you resolve mail.mydomain.com it will resolve 192.168.1.10 and externaly will resolve 80.23.23.23

You can't do this with an external DNS server.

---

