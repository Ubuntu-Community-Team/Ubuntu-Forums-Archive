---
title: "how can I configure sourcelist from local disk"
date: 2008-02-06
forum: Desktop Environments
---

### Post by linew on 2008-02-06
Can anyone help me? I want to configure source.lst to read package from local disk so every time when I install new package I will not need DVD(I copy everthing in DVD to Hard Disk)

---

### Post by MasterJS on 2008-02-06
You didn't need to do that. If you don't want to use the DVD, just go to SYSTEM > ADMINISTRATION > Software Sources. From there, you'll see all the repositories mostlikely checked if you did that, a lot of people check all of them because you get a vast amount of packages that you could install (its your choice). Now at the bottom, you should see Installable from CD/DVD and in the box you should see the name of your DVD. Uncheck and then go to terminal, type ```
sudo apt-get update
``` it will ask for your password, type it in, and then enter, and then the source.lst will update itself. After that, you can install any package, but it will have to download them from the internet first, which is basically what you would do for the majority of packages with the dvd anyway.

---

