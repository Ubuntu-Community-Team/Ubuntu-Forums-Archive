---
title: "Texmaker bug"
date: 2009-01-28
forum: General Help
---

### Post by optimisteo on 2009-01-28
Hi there,

I have a bug in texmaker which used to work perfectly right.

The gui crashes immediately after the texmaker splashscreen and the editor gui doesn't appear.
However the texmaker process is still running.

strace gives the following result:

```
read(7, 0x240b014, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(7, 0x240b014, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
```

Regards,

Opti

---

