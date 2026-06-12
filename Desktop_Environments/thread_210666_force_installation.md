---
title: "force installation"
date: 2006-07-07
forum: Desktop Environments
---

### Post by whiteB on 2006-07-07
Is there any way for installing force installation with dpkg -i option.
  My installation package is making conflicts with the core package.

---

### Post by mgor on 2006-07-07
```
dpkg --force-help
```

but i wouldn't recommend installing a package thats in conflict with another one, that might just break things.

---

