---
title: "VMWare Server 1.05 won't start"
date: 2008-12-02
forum: General Help
---

### Post by infernon on 2008-12-02
After a recent update, I rebooted my machine and found that VMWare Server refuses to start.  I am working in Gnome and can see the "placeholder" appear on the bar at the bottom of the screen telling me that VMWare is starting, but nothing happens afterwards.  

Does anyone know where I can look for clues as to what is preventing it from starting?

---

### Post by gape on 2008-12-05
> **infernon said:**
> After a recent update, I rebooted my machine and found that VMWare Server refuses to start.  I am working in Gnome and can see the "placeholder" appear on the bar at the bottom of the screen telling me that VMWare is starting, but nothing happens afterwards.  

Does anyone know where I can look for clues as to what is preventing it from starting?
i had problems with ... kernel headers or something
i did this
sudo /usr/bin/vmware-config.pl
and it works again
it complained about gcc beeing the vrong version, but it completed sucesfully and i can start vmware now

---

### Post by compiledkernel on 2008-12-05
Each time your machine updates the kernel packages, the vmware config needs to be rerun again. This is one of those annoying things about vmware server 1.x, 2.x etc.

---

### Post by infernon on 2008-12-06
Thanks guys.  I'm up and running.  Your help was much appreciated.

---

