---
title: "you have not chosen to trust &quot;GlobalSign Root CA&quot; - Citrix"
date: 2007-05-21
forum: Desktop Environments
---

### Post by hinge on 2007-05-21
Both my wife and I use citrix to connect to our separate workplaces. My citrix work like a charm but my wifes does not.
The problem is that when she tries to open an app (say outlook) the ICA connections window opens  along with an other progressbar window saying "contacting **servername**" - every thing looks just like when I connect to my workplace. 
BUT then she'll get an error message saying:
> "you have not chosen to trust "GlobalSign Root CA", the issuer of the server's security certificate"

I have seen that this seems to be an easy solvable issue....I went to:
[http://www.globalsign.net/securedby/check/](http://www.globalsign.net/securedby/check/)
and got a "new" certificate and did:

> sudo cp root.cacert /usr/lib/ICAClient/keystore/cacerts/globalsign.crt

But the problem persists....
I am running Kubuntu 704 with citrix client 10

Because of this I have to keep a VMware installation of windows - and thats not nice :(

---

### Post by heimo on 2007-05-21
Try renaming (EDIT: sorry, you already did this) the file from .cer to .crt, and if that doesn't help, see also this:
[http://www.griffith.edu.au/ins/griffithatanywhere/content07.html](http://www.griffith.edu.au/ins/griffithatanywhere/content07.html)

---

### Post by AreEK on 2007-08-22
I had a similar problem, and the solution was to simply copy the correct certificate from
/usr/share/ca-certificates/mozilla/GlobalSign_Root_CA.crt to /usr/lib/ICAClient/keystore/cacerts and set the owner to root. No other changes was nesescary.

---

### Post by Mykal73 on 2008-03-21
How do you pull this off in ubuntu 7.10? I installed the cert in firefox but it's still telling me I haven't chosen to trust the certificate issuer.

---

### Post by usererror on 2008-05-20
> **AreEK said:**
> I had a similar problem, and the solution was to simply copy the correct certificate from
/usr/share/ca-certificates/mozilla/GlobalSign_Root_CA.crt to /usr/lib/ICAClient/keystore/cacerts and set the owner to root. No other changes was nesescary.

Ah brilliant!  That fixed my issue, but with the Thawte_Premium_Server_CA.crt, since that is the one we use.

---

