---
title: "where are Firefox ssl certificates stored"
date: 2009-03-12
forum: General Help
---

### Post by b-boy on 2009-03-12
Hi 

When you acces secure website you need to accept a SSL certificate if you click on store certificate permernanty where in the file system does it store?

---

### Post by gdave on 2009-04-02
there's a system directory that mozilla apps will reference.  it's under /usr/share/ca-certificates/mozilla/

I'm not sure where user-imported certs are stored.

--EDIT--
looks like local user certs are stored in certs8.db in your profile directory.  anyone who knows more should chime in...

---

