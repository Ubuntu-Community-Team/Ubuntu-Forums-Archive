---
title: "Windows and Boot Sector"
date: 2009-03-08
forum: General Help
---

### Post by Java Geek on 2009-03-08
Hello, I need to reinstall windows with a fresh install which means to format C:\. I know how to reinitialize GRUB as bootloader, but will this install actuall kill the boot sector?

---

### Post by ajgreeny on 2009-03-08
I think so, yes, but as you say, it is easy to get it back.

---

### Post by Dysport on 2009-03-08
It will kill the boot sector, but as the actual boot manager GRUB is located on the linux partition, you can easily get it back with e.g. the super GRUB boot disc: [http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")

---

