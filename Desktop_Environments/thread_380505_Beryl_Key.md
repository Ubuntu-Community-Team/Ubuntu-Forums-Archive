---
title: "Beryl Key ???"
date: 2007-03-09
forum: Desktop Environments
---

### Post by Radu43 on 2007-03-09
W: GPG error: [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3FF0DB166A7476EA


How do I resolve this?

Thank you

---

### Post by Waappu on 2007-03-10
Hi

Type in terminal```
wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | sudo apt-key add -
sudo apt-get update
```

---

### Post by kigango123 on 2007-10-25
that seemed to work for me as well, thanks

---

