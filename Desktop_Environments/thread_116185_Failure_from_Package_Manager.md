---
title: "Failure from Package Manager"
date: 2006-01-12
forum: Desktop Environments
---

### Post by bobinski on 2006-01-12
I applied all the latest updates yesterday, and now I get this failure.  Does anyone know which package I need to re-apply/revert ...?

W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by kaamos on 2006-01-12
Try just hitting reload or do "sudo apt-get update" in a terminal.

---

### Post by bobinski on 2006-01-12
Reload Package Information did the trick.  (I must say, I thought I'd done that before)

---

