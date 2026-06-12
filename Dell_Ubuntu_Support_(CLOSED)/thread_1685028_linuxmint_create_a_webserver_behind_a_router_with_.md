---
title: "linuxmint create a webserver behind a router with static ip"
date: 2011-02-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by retano on 2011-02-10
Greetings everyone, 

Googled this, but get too many manuals for different distros so I am confused now (( If already asked please point me in a right direction.

I have a machine with LinuxMint 10 installed and would like to set up webserver on it. It is behind a router with LAN ips like 192.168.0.*, router model DLINK DIR 320 has a static ip 81.200.* delivered by my ISP. 

Things to be done:

1. Create a webserver to be visible from the outside via static ip 81.200.* (don't have a domain name yet). 
2. After a domain name is bought point webserver to that domain name, so everyone can access it from the outside. 
3. 80 port is forwarded, but looks like my ISP is blocking it, how can I proceed in this case?

Thank you.

pardon - please move to installations and upgrade section

---

### Post by retano on 2011-02-11
Allright, I did it )

1. Installed apache2, phpmyadmin
2. Copied the site into var/www
3. Restarted apache - I was able to see site on localhost
4. 80 port was not blocked - my router should be restarted to apply the rules. So I restarted it and everyone can access my test site now )

---

