---
title: "Limiting access to home directory"
date: 2006-03-04
forum: Desktop Environments
---

### Post by DonPachi on 2006-03-04
How do I restrict access to my home directory.  In example, I would like to create a guest account that cannot access /home/donpachi.

Will chmod -R 700 <dir> work or will it resrict access to programs from their config files there as well?

---

### Post by knalle on 2006-03-04
you can chmod your homedirectory to only you like this:

```

cd ~/
sudo chown -R yourusername.yourusergroup *
sudo chmod -R gu+rwX *
sudo chmod -R o-rwX *

```

---

### Post by DonPachi on 2006-03-04
Superb!  I searched around the forums for a while but could find nothing. Thanks very much for the quick reply.

---

### Post by knalle on 2006-03-04
happy to help :-)

---

### Post by Ramses de Norre on 2006-03-04
Are those commands the same as chmod -R 770 * ?
Or is there a difference between them?

---

