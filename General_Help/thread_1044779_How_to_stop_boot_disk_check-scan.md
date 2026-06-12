---
title: "How to stop boot disk check-scan?"
date: 2009-01-19
forum: General Help
---

### Post by offthegrid2 on 2009-01-19
I've searched but found nothing so I think I am not asking the right question(s).

I use encrypted hard disk and when it is time for the boot disk check it never works and results in my having to re-boot several times to bypass it.

Does anyone know how to disable this?

Thanks.

---

### Post by Yashiro on 2009-01-19
Change the trailing 1 on your boot partition in /etc/fstab to a 0.

For example@
> #/dev/sda1
UUID=bxxxxxx-3275-xxxx-xxxx-da35aa659c61     /               ext3        defaults,errors=remount-ro    0   **1**
to
> #/dev/sda1
UUID=bxxxxxx-3275-xxxx-xxxx-da35aa659c61     /               ext3        defaults,errors=remount-ro    0   **0**

---

### Post by offthegrid2 on 2009-01-19
Thank you. That was a big PITA.

---

