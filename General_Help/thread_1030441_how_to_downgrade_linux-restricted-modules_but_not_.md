---
title: "how to downgrade linux-restricted-modules but not kernel?"
date: 2009-01-04
forum: General Help
---

### Post by andresmh on 2009-01-04
The brightness adjuster on my laptop (thinkpad x300) shows up and it moves up and down but the actual brightness of the screen stays the same. This problem started happening after this update on Intrepid:
```
linux-restricted-modules-2.6.27-11-generic (2.6.27-11.15) to 2.6.27-11.16
linux-restricted-modules-common (2.6.27-11.15) to 2.6.27-11.16

```

What's interesting is that the actual update of the kernel to version 2.6.27-11 happened many days ago. It was only after updating the linux-restricted-modules and linux-restricted-modules-common packages that the brightness adjusting stopped working.

A quick solution was to use grub to boot using the older kernel, but I want to use the new kernel. Especially since it seems like the problem is not with the kernel itself.

Is there a way to downgrade only the offending packages?

---

### Post by andresmh on 2009-01-11
Bump

---

