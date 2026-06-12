---
title: "Root Nautilus No Network Connection"
date: 2022-02-07
forum: Desktop Environments
---

### Post by Geoff_Lane on 2022-02-07
Folks,

I often access a Raspberry Pi from my 20:04 Ubuntu system using ssh or occasionally Nautilus using the 'other locations' option and sftp://

If I launch Nautilus as sudo any input into other locations remains in red and the connect button is not enabled.

This appears to be a network issue when in sudo mode, my network connections are shareable, is there something I have to enable under sudo?

Thanks in advance.

Geoff

---

### Post by ActionParsnip on 2022-02-09
If you map the share then you don't need sudo. You just need execute access to the mount path before you mount it (if memory serves). Does that help?
```

sudo chmod +x /path/to/mount/point

```

Obviously change the path to the actual folder you are using.

---

