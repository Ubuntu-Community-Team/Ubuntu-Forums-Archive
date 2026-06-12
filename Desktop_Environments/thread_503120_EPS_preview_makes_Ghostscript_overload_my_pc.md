---
title: "EPS preview makes Ghostscript overload my pc"
date: 2007-07-17
forum: Desktop Environments
---

### Post by Icarosaurus on 2007-07-17
When I open a folder with eps files, nautilus tries do generate a thumbnail: "gs" process (ghostscript) takes 1,0GB of swap and the hdd light stays on.  My machine's performances slow down and I have to terminate gs for making system usable.
Anyone had the same problem and solved it?
Thank you.

---

### Post by kisiyel on 2007-08-04
> **Icarosaurus said:**
> When I open a folder with eps files, nautilus tries do generate a thumbnail: "gs" process (ghostscript) takes 1,0GB of swap and the hdd light stays on.  My machine's performances slow down and I have to terminate gs for making system usable.
Anyone had the same problem and solved it?
Thank you.

That's a bug in gs-esp.

Try to "install gs-gpl" from synaptic and  make it your main gs with "sudo update-alternatives --config gs".

Good luck...

---

### Post by Icarosaurus on 2007-08-28
thank you... seems to work

---

