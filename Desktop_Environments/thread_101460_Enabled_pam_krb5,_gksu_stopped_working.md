---
title: "Enabled pam_krb5, gksu stopped working"
date: 2005-12-09
forum: Desktop Environments
---

### Post by Fault Bucket on 2005-12-09
After setting up everything to use Kerberos auth, I now cannot launch apps through gksu.  Everything else with krb5 works great - initial login, xscreensaver, forwarding TGTs to other kerberized hosts, etc.

I've straced gksu and it looks like it's trying to request credentials for 'root@MY.KERBEROS.DOMAIN'.  The graphical password request box never appears on-screen.

I can still launch items like synaptic using normal sudo from a command line.

Any ideas?

-chris

---

