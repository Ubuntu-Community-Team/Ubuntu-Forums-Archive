---
title: "Dialup Connection"
date: 2006-07-08
forum: Desktop Environments
---

### Post by masood on 2006-07-08
How can i create dialup connection in Ubuntu? and how can i check that my dialup modem is properly installed or not?

regads,

---

### Post by hajk on 2006-07-08
The easiest way is to use the System -> Administration -> Networking menu. If your modem is recognized, there will be an interface ppp0 that you can highlight and then configure by selecting Properties. Afterwards, you can then Activate the ppp0 interface, and you should hear it dial (if you also configured the modem sound).

Now, if there is no ppp0 interface, then you may have a driver problem. In that case you should give more information on the modem type.

---

