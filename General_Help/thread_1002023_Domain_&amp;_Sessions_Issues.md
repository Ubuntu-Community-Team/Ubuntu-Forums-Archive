---
title: "Domain &amp; Sessions Issues"
date: 2008-12-04
forum: General Help
---

### Post by OldManRiver on 2008-12-04
All,

I develop for a customer on DT using WAMP.  Test box is U-Server 7.10.  Production environment is RHE4.  Current Problems are with Test box.

I was having compatibility issues and got error messages to that effect so went to php.ini file and changed 1 to 0 for following lines:```
session.bug_compat_42 = 0
session.bug_compat_warn = 0

```then restarted Apache.

Apache gave me the following errors:>  * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 192.168.1.70 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 192.168.1.70 for ServerName

The customer's firewall has domain-name of:
> test.homedomain.comNot much of Apache head so what do I need to do to make this error go away?

Also having session vars handling issues between the version.  DT with WAMP Server 2.0 is error free.  Test box give variety of errors.  Most center around the fact that shopping cart is housed in an IFRAME and there is combo of both straight $_SESSION vars and OOP Classes, with some OOP Classes also being assigned to session vars, which is not working at all, especially the shopping cart basket vars.

All help appreciated!

OMR

---

### Post by OldManRiver on 2009-02-28
02/28/09
Man it sure is great that I can solve my own problems!

05/16/09
I was being cheecky in Feb, but so old now forgot what I did to resolve this.

OMR

---

