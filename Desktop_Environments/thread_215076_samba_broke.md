---
title: "samba broke"
date: 2006-07-13
forum: Desktop Environments
---

### Post by nullspace on 2006-07-13
I am not sure if this was due to a bug or not but I tried to access my machine from a windows client and it failed to connect. so I looked through my settings and every thing seemd fine. I then though maybe I forgot to add a password or some how it broke so I did a smbpasswd <username> and input the passwords and go this.

```
Unable to open/create TDB passwd
pdb_getsampwnam: Unable to open TDB passwd (/var/lib/samba/passdb.tdb)!
Failed to find entry for user <username>.
Failed to modify password entry for user <username>


```

I figured alright fine I'll just add myself manualy only to realise that passdb.tdb isn't even there. Does anyone have any ideas to remedy the situation.

---

