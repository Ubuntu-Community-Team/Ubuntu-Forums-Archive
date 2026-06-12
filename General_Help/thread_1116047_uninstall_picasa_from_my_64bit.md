---
title: "uninstall picasa from my 64bit"
date: 2009-04-04
forum: General Help
---

### Post by Heeter on 2009-04-04
Hi all,

I am wondering how do I remove picasa from my system?

I used the one click deb package install from google.

Thanks

Heeter

---

### Post by dtoronto on 2009-04-04
I believe you can:

```
sudo apt-get --purge remove <package>
```

picassa should be in the Ubuntu repos.  You also might be able to find it in synaptics manager and remove it that way.
If it's not in the repos you may need to try rm -R.

---

### Post by Heeter on 2009-04-04
Thanks for your help dtoronto,

Much appreciated.


Heeter

---

