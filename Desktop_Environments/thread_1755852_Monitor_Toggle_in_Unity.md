---
title: "Monitor Toggle in Unity"
date: 2011-05-11
forum: Desktop Environments
---

### Post by nadeepa on 2011-05-11
I can't use function key combination to toggle between connected monitor and laptop monitor of my Dell N4010, running Ubuntu Natty.

This happens in Unity interface only. In gnome (Ubuntu classic), function key combination works fine.

When I press Fn+F1, it acts similar to pressing super+F1.

Any workaround this?

---

### Post by nadeepa on 2011-05-31
bump

---

### Post by michael81 on 2011-06-12
Hi,

I found the solution to this problem here:

[https://bugs.launchpad.net/oem-priority/+bug/539477](https://bugs.launchpad.net/oem-priority/+bug/539477)


I updated the GRUB_CMDLINE_LINUX line in /etc/default/grub to:

GRUB_CMDLINE_LINUX="acpi_osi=\"!Windows 2009\""

Then ran update-grub. After restarting I was able to toggle the display using the Fn key.

Regards,
Michael

---

