---
title: "Citrix logon issues Ubuntu 14.04LTS"
date: 2015-03-24
forum: Desktop Environments
---

### Post by biased99 on 2015-03-24
A couple of years back, I used to the use the notebook on which I'm typing this. At the time it was running (I think) 10.04 (or something around there), and the then-current version of Firefox. 

Of course, I've upgraded a few times since then, and now I can't for the life of me get the thing to allow me to login to my work's Citrix environment. I keep getting error 61, with a particular Certificate not being trusted. (Cert. in question is Verisign Class 3 Public Primary Certification Authority - G5. For the record, this is listed in the Browser's Certficate settings, and is checked to authorise SW, Web sites and mail.

Things I've tried:

Re-install the Citrix client (both via the cli and by using a .deb package through the SW Centre).

Ensured that the Certificate Authority is trusted (see above).

Manually imported the appropriate certificate file (pca3-g5ss.crt) directly into /usr/lib/ICAClient/keystore/cacerts

Have also installed Chrome (directly from their web site). Has the same issues, so suggest a cacerts issue...but I'm st*ffed if I know what that might be. 

Would appreciate any help anyone might be able to give.

TIA.

---

### Post by biased99 on 2015-04-02
So, no-one has any idea about how to resolve this issue...?

---

### Post by QIII on 2015-04-02
You might get better action on your question if you didn't wait a week to bump it.  If you haven't gotten a response in about 12 hours, just add another post with the word "bump".

That'll bring your thread back to the surface.

Cheers!

---

