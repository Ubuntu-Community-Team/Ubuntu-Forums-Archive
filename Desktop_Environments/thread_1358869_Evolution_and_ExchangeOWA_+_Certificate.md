---
title: "Evolution and Exchange/OWA + Certificate"
date: 2009-12-18
forum: Desktop Environments
---

### Post by deadland on 2009-12-18
Dear ubuntu-frinds,

I used Evolution with Exchange/OWA-Server from the company where I'm working, but since they changed the configuration I can't get it working any more.

That's the configuration for MS Outlook:

General:
```
Microsoft Exchange Server= cluexvs1.domain.de
```

Advanced:
```
Use cached Exchange Mode= ON
Download shared folders= ON
Download Public folder Favourites= ON
```

Security:
```
Encrypt data between Microsoft Office Outlook and Microsoft Exchange=ON
Logon network security= Password Authentication (NTLM)
```

Connection:
```

Connect to Microsoft Exchange using HTTP= ON
```

Exchange Proxy Settings ...:

```
Use this URL to connect to my proxy server for Exchange: https://owarpc.domain.de
Connect using SSL only= ON (**Thats new!!!!**)
Only connect to proxy server that have this principa name in their certificate: msstd:owa.domain.de (**Thats new!!!**)

Use this autentication when connectiong to my proxy server for Exchange: NTLM Authentication
```

Well since they added the new requierments, I can't even create the account. Someone know where I can add this certificate thing (**msstd:owa.domain.de**)?

Thanks in advanced

---

### Post by deadland on 2009-12-30
Anyone know how to "emulate" this option:

```
only connect to proxy server that have this principal name in their certificate: msstd:owa.domain.de
```

---

### Post by CK0y0TE on 2010-01-25
Well, same here. msstd is in the configuration, appearantly we do need it. How can we get through this new Exchange proxy with Evolution? :confused:

---

### Post by goldwein on 2010-03-10
> **CK0y0TE said:**
> Well, same here. msstd is in the configuration, appearantly we do need it. How can we get through this new Exchange proxy with Evolution? :confused:
Having the same issue.  Has anyone resolved this?

---

### Post by yes_i_bunt_too on 2011-08-05
Has anybody solved this?  I'm attempting this right now with fail.

---

