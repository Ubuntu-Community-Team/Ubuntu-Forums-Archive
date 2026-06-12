---
title: "how to edit udev to reduce boot time?"
date: 2009-03-09
forum: General Help
---

### Post by chanyunkwan on 2009-03-09
After disabling fsck on bootup, boottime reduce to 23sec from 48sec.

I was told by a friend to edit the udev like this way.

```
open /etc/init.d/udev and find "udevadm" string. Comment it and
use the line to replace:
(let udev do not read rule file and make all of device file again)
cp -R /lib/dev/* /dev

Next step, using "lsmod" to get all of modules what is used, and try to
set them in /etc/modules.
(let udev do not read rule file to load modules)

```

but I am kind of confused by the udev. There're several udevadm in it. I don't really know how make it not to read rule file and make all of device file again.

Thank you

---

