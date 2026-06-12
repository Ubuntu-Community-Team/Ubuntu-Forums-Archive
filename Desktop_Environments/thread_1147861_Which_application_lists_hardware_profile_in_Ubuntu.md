---
title: "Which application lists hardware profile in Ubuntu?"
date: 2009-05-03
forum: Desktop Environments
---

### Post by maporojo on 2009-05-03
Which application may I download to view the hardware profile of my computer? I have heard of it but I cannot remember the name. I know of using "sudo lshw" but I would also like to have that application listed under "System > Preferences" or wherever the line "sudo apt-get ..." will put it in the menus. Thanks.

---

### Post by doas777 on 2009-05-03
I use lshw-gtk. you can install it from synaptic or the add/remove tool.
it will create a launcher in your Applications->Systems Tools menu, but you can edit your menus and add an entry under System -> Preferences with the command:```
gksu lshw-gtk
```

---

### Post by maporojo on 2009-05-03
Thanks for the response. I installed "Hardware Lister" and it appears to be a GUI version of lshw. There is another application that has a better interface but I may have to Google my way to find it.

---

### Post by pbpersson on 2009-05-03
I use HardInfo and it appears in the menus as System-->Preferences-->System Profiler and Benchmark

---

### Post by doas777 on 2009-05-04
> **maporojo said:**
> Thanks for the response. I installed "Hardware Lister" and it appears to be a GUI version of lshw. There is another application that has a better interface but I may have to Google my way to find it.


as a general rule, google before you create a thread.

---

### Post by maporojo on 2009-05-05
Thanks everyone. I installed and prefer "hardinfo".

---

