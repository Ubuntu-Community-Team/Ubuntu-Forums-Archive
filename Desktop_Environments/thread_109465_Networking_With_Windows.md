---
title: "Networking With Windows"
date: 2005-12-28
forum: Desktop Environments
---

### Post by dwessell on 2005-12-28
Hi Ubuntu People.

Having read the quick guide, and the docs, I'm left with one question.. In order for me to network an ubuntu install with other Windows computer, do I need Samba installed? Or is that only if the Ubuntu install is acting as a server?

Thanks
David

---

### Post by cwaldbieser on 2005-12-28
[QUOTE=dwessell]Hi Ubuntu People.

Having read the quick guide, and the docs, I'm left with one question.. In order for me to network an ubuntu install with other Windows computer, do I need Samba installed? Or is that only if the Ubuntu install is acting as a server?

Thanks
David[/QUOTE]
You only need smbd installed if you want Ubuntu to be the server.  Otherwise, you should be able to simply access shares with a "SMB://..." URL.

---

### Post by dwessell on 2005-12-28
It's a standard Windows workgroup... Will that work for a Windows workgroup as well?

Thanks
David

---

