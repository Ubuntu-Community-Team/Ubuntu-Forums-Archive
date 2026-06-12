---
title: "Can you tell me what the people at launchpad.net mean by this:"
date: 2009-04-28
forum: General Help
---

### Post by hotweiss on 2009-04-28
Can you tell me what the people at launchpad.net mean by this:

[https://bugs.launchpad.net/ekiga/+bug/368179/comments/5](https://bugs.launchpad.net/ekiga/+bug/368179/comments/5)

I filed a bug for the problem I was having with Ekiga:

[https://bugs.launchpad.net/ekiga/+bug/368179](https://bugs.launchpad.net/ekiga/+bug/368179)

---

### Post by dcstar on 2009-04-29
> **hotweiss said:**
> Can you tell me what the people at launchpad.net mean by this:

[https://bugs.launchpad.net/ekiga/+bug/368179/comments/5](https://bugs.launchpad.net/ekiga/+bug/368179/comments/5)

I filed a bug for the problem I was having with Ekiga:

[https://bugs.launchpad.net/ekiga/+bug/368179](https://bugs.launchpad.net/ekiga/+bug/368179)

It means the particular SIP provider you are using does not have their DNS server set up in the way the software expects it to be, so use the IP address instead of the DNS name.

---

### Post by hotweiss on 2009-04-29
> **dcstar said:**
> It means the particular SIP provider you are using does not have their DNS server set up in the way the software expects it to be, so use the IP address instead of the DNS name.

I tried the IP address, and it didn't work.

---

### Post by hotweiss on 2009-04-29
Sorry, it did work. I was making calls from the call history which still had @sip.poivy.com. When I made a new call, Ekiga used the new IP address. Thanks for all the help everybody.

---

