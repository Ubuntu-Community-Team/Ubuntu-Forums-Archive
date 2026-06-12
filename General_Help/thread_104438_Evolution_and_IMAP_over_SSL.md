---
title: "Evolution and IMAP over SSL"
date: 2005-12-16
forum: General Help
---

### Post by teclis on 2005-12-16
I have problems connecting to a IMAP-server via SSL. SMTP via TLS works without any problems.

The Server listens on Port 993 (SSL), but I can't connect.

Maybe SSL needs additional packages? :???: Does anyone know a good tutorial?

Teclis

---

### Post by kosmic on 2005-12-16
Do you have any firewall or Router blocking that port ??

---

### Post by nocturn on 2005-12-16
I'm using this setup without a problem... (my own Cyrus IMAP server).

You can test the ssl connection with openssl client.

---

### Post by teclis on 2005-12-16
[QUOTE=kosmic]Do you have any firewall or Router blocking that port ??[/QUOTE]

Yes, a router is before the PC, but all outgoing Connections are permitted.

---

### Post by teclis on 2005-12-16
[QUOTE=nocturn]I'm using this setup without a problem... (my own Cyrus IMAP server).

You can test the ssl connection with openssl client.[/QUOTE]
I'm not a very experienced Linux-User. Where can I get a ssl-client or which package should I install?

And what must I type in the console?

---

### Post by teclis on 2005-12-16
OK, in my case I ignored the Portnumber. Evolution accepts the Portnumber in the form "domain.com:993". Thunderbird has an additional formfield for the portnumber. A little bit confusing.

Thanks for your help. :)

---

