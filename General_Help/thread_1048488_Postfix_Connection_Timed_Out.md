---
title: "Postfix Connection Timed Out"
date: 2009-01-23
forum: General Help
---

### Post by qoar on 2009-01-23
Hello,

I am running/setting up an Ubuntu Server. I am using it as a web server and a mail server.

My apache is working perfectly but postfix is giving me a ton of trouble. I am able to receive email messages to my domain (server) but I can not reply (using sendmail or SMTP). Also, I can not access my email accounts via POP (only local access).

My internet service provider has NOT blocked port 25 and I am not sure what is wrong.

Thanks so much for helping!!

---

### Post by HermanAB on 2009-01-23
Postfix is only a MTA.  If you want POP/IMAP, then you need to install Dovecot as well.  However, you find it much easier to simply abandon Postfix and install Citadel instead.

For a mail server to send mail successfully, you need to have the hostname and DNS configured properly.  The DNS MUST have A, MX and PTR records.  Test the DS with digg and nslookup.

See these: 
[http://www.citadel.org](http://www.citadel.org)
[http://aeronetworks.ca/citadel-clients.html](http://aeronetworks.ca/citadel-clients.html)
[http://aeronetworks.ca/citadel-howto.html](http://aeronetworks.ca/citadel-howto.html)

Cheers,

Herman

---

