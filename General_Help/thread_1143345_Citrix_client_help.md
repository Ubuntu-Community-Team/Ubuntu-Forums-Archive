---
title: "Citrix client help"
date: 2009-04-29
forum: General Help
---

### Post by pdipizzo on 2009-04-29
I need Citrix to access my work server, so I installed the Terminal Server client and the MetaFrame Presentation Server Client for Linux. It all installed and loads properly, but when I access the server, I get the following error message: 

"You have not chosen to trust "/C=US/ST=/L=/0=Equifax/0U=Equifax Secure Certificate Authority/CN=", the issuer of the server's security crtificate (SSL error 61)."

Unfortunately, as usual, my IT department refuses to touch anything but Windows or Mac, so I need someone to guide me in a non-esoteric way to find the solution to this problem.

Thanks for any help.

---

### Post by Rede on 2009-05-19
sudo cp /usr/share/ca-certificates/mozilla/* /usr/lib/ICAClient/keystore/cacerts/

---

