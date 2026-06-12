---
title: "umount on hibernate, mount on resume."
date: 2005-12-30
forum: General Help
---

### Post by mrkslntbob on 2005-12-30
I have a shared fat32 partition for windowsxp and ubuntu linux, i want to unmount it when i hibernate the laptop, and have it remounted on resume.
 
i looked in /etc/default/acpi-support and didn't see a section for that.

does anyone else know where to set this?

thanks.

---

### Post by schilcha on 2005-12-30
I've never tried this (hibernation wont work on my machine), but here's my suggestion:
write a little script to mount/umount the fat32 partition, e.g.
```

#!/bin/sh
umount /media/your-win-mount

```
and put them in /etc/acpi/suspend.d and /etc/acpi/resume.d. Their names need to end with ".sh"

Have a look at the end of /etc/acpi/prepare.sh and the beginning of /etc/acpi/resume.sh. That's where everything in the two directories is sourced.

Good Luck!

---

### Post by mrkslntbob on 2006-01-05
Thanks schilcha.

That's exactly what I needed to know.

---

