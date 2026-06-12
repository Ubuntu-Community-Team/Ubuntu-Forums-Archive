---
title: "Log files that make install creates?"
date: 2009-03-01
forum: General Help
---

### Post by MacUntu on 2009-03-01
Is there a way to log all files that "make install" installs? My gut's telling me that "make uninstall" doesn't remove everything for the package I'm compiling.

"make install --dry-run" creates a lot of script output but I'd only need the concrete files that are touched/created.

---

### Post by snova on 2009-03-01
No, I don't think so. But try [checkinstall]("https://wiki.ubuntu.com/CheckInstall").

---

### Post by MacUntu on 2009-03-03
Great, thanks! Helped a lot!

---

