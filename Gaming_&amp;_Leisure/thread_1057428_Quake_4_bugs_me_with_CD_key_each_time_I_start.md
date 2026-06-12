---
title: "Quake 4 bugs me with CD key each time I start"
date: 2009-02-01
forum: Gaming &amp; Leisure
---

### Post by x1a4 on 2009-02-01
Hi,
I installed the latest Linux Quake 4 and it works great, except that it keeps bugging me for the CD key each time I run it.  How can I stop this?  Yes it is a legal copy.  Doom 3 does the same thing but only once for each user account that runs it.  

Thank you.

---

### Post by kutagh on 2009-02-02
Try editing the config files directly to put in the cd-key. It apparantly doesn't save it there.

---

### Post by x1a4 on 2009-02-06
Thanks for the idea kutagh but that's not it.  The key is saved correctly in ~/.quake4/q4base/quake4key.  The trouble was my firewall.  It's configured to be border-line paranoid and didn't let Quake access the authentication server.  Once I allowed it to "call home" and authenticate itself everything started to work well.

---

