---
title: "shares-admin broken"
date: 2005-12-31
forum: General Help
---

### Post by musther on 2005-12-31
shares-admin just hangs, and hangs, and hangs....  

No terminal output, no nothing, just hangs, I can run it as root, or using sudo, nothing.

I've tried re-installing the package, but nothing.

---

### Post by zoiks on 2005-12-31
Just a guess, but maybe it needs libsmbclient, or samba-common, and stuff like that before it will run?  The first time I ran it, it wanted to install some smb stuff and nfs stuff before proceeding.  Maybe this check is broken on your system.

---

### Post by musther on 2006-01-01
Thanks for the guess, but I have all of them installed.

---

