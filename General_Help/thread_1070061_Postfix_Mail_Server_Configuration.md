---
title: "Postfix Mail Server Configuration"
date: 2009-02-14
forum: General Help
---

### Post by dstu69 on 2009-02-14
Hello,

I want to use my Ubuntu Server (7.10) as my mail server for 3 domains that we use, which I set in /etc/postfix/main.cf:
> myhostname = mail.mydomain.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mydomain.com,my2nddomain.com,my3rddomain.com
mynetworks = 127.0.0.0/8

I configured 3 virtual interfaces/IP addresses (one for each domain) and I want to create users for the emails account, but not as Linux users.

I installed Webmin (I'm not a big Linux CLI expert, so it seems easier).

Can anyone please help me set it up to do the following?
1. Create mail users, such as:
   [email]user1@mydomain.com[/email]
   [email]user2@mydomain.com[/email]
   [email]user1@my2nddomain.com[/email]
   [email]user1@my3rddomain.com[/email]
   ...
2. Set the SMTP server so that when sending an email, it would use a specific IP address (preferably a different one for each domain, but it's not critical, if it's not possible).
3. Set the server to accept SMTP for authenticated users from anywhere.
4. Set several IP addresses or subnets to allow emails without authentication.

Thank you in advance,

David

PS. Please use simple explanations, because I'm not an expert on Linux (to say the least).

---

### Post by hyper_ch on 2009-02-14
have a look at [http://www.howtoforge.com](http://www.howtoforge.com) --> there are many howtos for running postfix with virtual users.

---

### Post by dstu69 on 2009-02-15
> have a look at [http://www.howtoforge.com](http://www.howtoforge.com) --> there are many howtos for running postfix with virtual users. 

Thank you for your recommendation, but the articles I found there discuss a complicated script of a clean installation from scratch, with MySQL for users/domains listing.

Isn't there a simple way to create a text file to include this data?

Thanks,

David

---

### Post by hyper_ch on 2009-02-15
I don't think so... either system users for delivery or mysql

---

