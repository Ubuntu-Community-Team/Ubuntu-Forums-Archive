---
title: "computer under attack?  help!"
date: 2006-09-26
forum: Desktop Environments
---

### Post by cypher35 on 2006-09-26
I have recently taken a look at my ftp logs from proftpd and noticed that someone with ip address **218.30.22.249** keeps trying to brute force their way in to a non-existant "Administrator" account.

I looked up their ip address, found that it has an ftp server running on it as well as a paypal phishing web portal.  I can only imagine what nefarious purposes this scumbag has in trying to access my computer.

While i know that they will likely never succeed (since obviously, there is no such account), I would like to know if there is any way to filter out any incoming traffic from that ip address and essentially enter stealth mode when it tries to perform port scans or brute force attacks.

Any suggestions?

---

### Post by mozetti on 2006-09-26
Use synaptic/aptitude/apt-get to install firestarter. It's a GUI front-end for linux's built-in firewall, iptables. Then, just block all traffic from that IP.

---

### Post by skymt on 2006-09-26
Or use Firehol if you'd rather use a tool that doesn't use a GUI, or flash at you every time it blocks something.

---

### Post by whizbaby on 2006-09-26
You can simply add the IP to your */etc/hosts.deny* by copy-pasting this line into it (in your favorite text editor):

ALL: 218.30.22.249

Sure there are some scripts that can recognize such attacks and add to /etc/hosts.deny automatically (look over net to find one suitable for you).

---

### Post by cypher35 on 2006-09-26
thanks for the quick replies.  i'll try a few of your suggestions and find which option suits me.

---

### Post by denzilla on 2006-09-26
You should report his sorry *** on the phishing portal. I'm sure Paypal would love to take care of it :)

---

### Post by dentaku65 on 2006-09-26
> **cypher35 said:**
> I have recently taken a look at my ftp logs from proftpd and noticed that someone with ip address **218.30.22.249** keeps trying to brute force their way in to a non-existant "Administrator" account.

I looked up their ip address, found that it has an ftp server running on it as well as a paypal phishing web portal.  I can only imagine what nefarious purposes this scumbag has in trying to access my computer.

While i know that they will likely never succeed (since obviously, there is no such account), I would like to know if there is any way to filter out any incoming traffic from that ip address and essentially enter stealth mode when it tries to perform port scans or brute force attacks.

Any suggestions?

Install **nikto** and **nmap** and kill by yourself that bug! 8) :twisted:

---

### Post by mozetti on 2006-09-27
> **skymt said:**
> Or use Firehol if you'd rather use a tool that doesn't use a GUI, or flash at you every time it blocks something.

Actually, if you install Firestarter from synaptic/aptitude/apt-get you don't need to run it all the time. Run it, make your changes, close it -- the changes to the iptables stay the same and it become part of the startup process.

So, the flashing part isn't correct and the GUI would only be used when making changes to your firewall policies.

---

