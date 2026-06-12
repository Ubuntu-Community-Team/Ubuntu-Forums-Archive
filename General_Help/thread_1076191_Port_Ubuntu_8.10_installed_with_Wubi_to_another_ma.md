---
title: "Port Ubuntu 8.10 installed with Wubi to another machine"
date: 2009-02-21
forum: General Help
---

### Post by voodoo_doctor on 2009-02-21
Hey,

I was wondering if it is possible to port Ubuntu 8.10 installed with Wubi to another machine? Theoretically it shouldn't be difficult: just install Ubuntu with Wubi on the other machine and then overwrite the files with the files from the old machine. But is it really that easy? I guess someone tried that already. All kind of help is appreciated. :D

Edit: It is worth noticing that the hardware configuration is pretty much the same on the machines (Just bigger hdd, more ram and faster cpu.)

---

### Post by voodoo_doctor on 2009-02-23
Nothing?

---

### Post by theozzlives on 2009-02-23
I'd try Remastersys

---

### Post by azmo35 on 2009-02-23
Hi,maybe LVM or Clonezila [here]("http://www.clonezilla.org/").

---

### Post by robhemmerich on 2009-04-08
I am interested in accomplishing the same thing. Here's what I tried -- this didn't work, just to be clear!

1. Install Wubi on machine. 
2. Spend hours configuring, downloading, and otherwise using the Ubuntu install.
3. From Windows, make a copy of root.disk and swap.disk. 
4. Uninstall Wubi, then reinstall Wubi on the same machine.
5. Boot into Ubunutu to let the installation of Ubuntu complete.
6. Boot into Windows. Overwrite the fresh root.disk and swap.disk with the old root.disk and swap.disk saved in step 3.
7. Boot into Ubuntu. The world is not a happy place, as the machine fails to fully boot up with lots of fatal errors etc.

My current theory is that either
- I should have completed step 6 before step 5
- I should have only overwritten root.disk? (Don't think so).
- This isn't possible, at least not in the way I am describing.

Alternative opinions are warmly welcomed!

---

