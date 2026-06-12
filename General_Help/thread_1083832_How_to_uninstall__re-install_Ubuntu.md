---
title: "How to uninstall / re-install Ubuntu?"
date: 2009-03-01
forum: General Help
---

### Post by noseforsharpies on 2009-03-01
I want to uninstall then re-install Ubuntu; going from the 32-bit to the 64-bit. How do I accomplish this?

---

### Post by taurus on 2009-03-01
Boot from the x86_64 LiveCD and at the partition screen, pick Manual option and tell the installer to mount whichever partition that you use for root filesystem before to / and format it.  Remember, you must mount it to / or the installer will complain about no root filesystem declared.

---

