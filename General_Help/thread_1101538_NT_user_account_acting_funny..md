---
title: "NT user account acting funny."
date: 2009-03-20
forum: General Help
---

### Post by lithiumKid1976 on 2009-03-20
hi
im currently trying (as a work project) to see how easy it is to intergrate ubuntu into our windows enviorment, and so far so good, i have added the machine to the active directory, and can log on using my NT account.

Remote desktop and mapping shares all work well :)

i have noticed though, and it may be something ive done,
but when i fire up the terminal i get this error.

id: cannot find name for group ID 897592711

also when trying to connect the printers, it keeps asking me for the password for "root", which is kinda strange as i thought it would have been asking me for the password for the user account i created at build time?

this only seems to happen when logged on to the domain, when logged on locally to the pc it seems to be fine.
any suggestions?

---

### Post by lithiumKid1976 on 2009-04-07
the new version of likewise (5249) sorted this issue.
i no longer get that error when using the terminal or other apps.

---

