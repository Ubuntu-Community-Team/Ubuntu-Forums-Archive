---
title: "Any syntax guru's???"
date: 2009-02-25
forum: General Help
---

### Post by johnson8707 on 2009-02-25
Is there a value I can put in the FSTAB that tells it to mount an SMB share with the users login username and password? (i.e. %u or %p etc)

I would like to do this so when the machine mounts the SMB share it mounts with THEIR credentials instead of one I specify.

Thanks! :D

---

### Post by Blice on 2009-02-25
FSTAB gets read and the drives get mounted before anyone logs in, this happens during boot. If you wanted to use username/password you would have to do it when Gnome starts up, though I'm not sure how you would fetch the user's password.

---

