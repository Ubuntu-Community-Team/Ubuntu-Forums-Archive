---
title: "Want to setup a web and mail server on desktop environment."
date: 2011-05-27
forum: Desktop Environments
---

### Post by Dutchbeer on 2011-05-27
Before setting up a dedicated web- and mail-server system, I want to learn it by setting both up on my desktop environment. So far I can only find how-to's which are based on server install iso's. 

Is it wise first to install a mail server by using i.e. [http://flurdy.com/docs/postfix/]("http://flurdy.com/docs/postfix/"). Get it up and running and then install a lamp server using [http://www.lullabot.com/videos/install-local-web-server-ubuntu]("http://www.lullabot.com/videos/install-local-web-server-ubuntu") or [http://www.akker-huis.nl/ubuntu-installeren-lamp.php]("http://www.akker-huis.nl/ubuntu-installeren-lamp.php").
[CENTER]:confused:[/CENTER]

Both servers must use my own IP address which is related to my own domain xxxxx.com I also need to understand how to incorporated these.

My desktop is Ubuntu 11.04 2.6.38-8-generic x86_64.

Can anybody put me in the right direction?

---

### Post by collisionystm on 2011-05-27
> **Dutchbeer said:**
> Before setting up a dedicated web- and mail-server system, I want to learn it by setting both up on my desktop environment. So far I can only find how-to's which are based on server install iso's. 

Is it wise first to install a mail server by using i.e. [http://flurdy.com/docs/postfix/]("http://flurdy.com/docs/postfix/"). Get it up and running and then install a lamp server using [http://www.lullabot.com/videos/install-local-web-server-ubuntu]("http://www.lullabot.com/videos/install-local-web-server-ubuntu") or [http://www.akker-huis.nl/ubuntu-installeren-lamp.php]("http://www.akker-huis.nl/ubuntu-installeren-lamp.php").
[CENTER]:confused:[/CENTER]

Both servers must use my own IP address which is related to my own domain xxxxx.com I also need to understand how to incorporated these.

My desktop is Ubuntu 11.04 2.6.38-8-generic x86_64.

Can anybody put me in the right direction?

You should be installing virtualbox and testing all of this. Not on your actual Natty install.

I suggest you use something like Zentyal. [www.zentyal.com](www.zentyal.com)

its is based on 10.04 and will do everything you want. Plus it is managed in a nice web interface and has good support / documentation. I am sure you will find it satisfactory.

---

### Post by Dutchbeer on 2011-05-28
> **collisionystm said:**
> You should be installing virtualbox and testing all of this. Not on your actual Natty install.

I suggest you use something like Zentyal. [www.zentyal.com](www.zentyal.com)

its is based on 10.04 and will do everything you want. Plus it is managed in a nice web interface and has good support / documentation. I am sure you will find it satisfactory.


Thanks, will try it. :P

---

