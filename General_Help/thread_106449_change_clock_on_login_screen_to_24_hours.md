---
title: "change clock on login screen to 24 hours?"
date: 2005-12-20
forum: General Help
---

### Post by bigblop on 2005-12-20
When I log into Ubuntu the clock is in 12 hours, how do I change it to 24 hours?

---

### Post by Gandalf on 2005-12-20
open /etc/gdm/gdm.conf
at amost line 374 you will find something like
```

# Always use 24 hour clock no matter what the locale.
#Use24Clock=false

```

uncomment
```

#Use24Clock=false

```

save and reboot

---

### Post by bigblop on 2005-12-20
don't you mean uncomment and change to:

Use24Clock=true


this does not work and does not make much sense:
Use24Clock=false

---

### Post by Gandalf on 2005-12-20
[QUOTE=bigblop]don't you mean uncomment and change to:

Use24Clock=true


this does not work and does not make much sense:
Use24Clock=false[/QUOTE]
Yep sorry for that i forget to mention it :oops:

---

