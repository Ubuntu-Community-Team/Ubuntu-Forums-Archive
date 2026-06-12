---
title: "How can I read/write a floppy?"
date: 2009-01-07
forum: General Help
---

### Post by glenngds2007 on 2009-01-07
I must not have my system configured correctly and/or have the correct packages installed.  Could someone tell me how it is done, please? :confused: I am running Ubuntu 8.10...  When I open Places>Computer it does not show floppy at all.

---

### Post by plucky on 2009-01-07
> **glenngds2007 said:**
> I must not have my system configured correctly and/or have the correct packages installed.  Could someone tell me how it is done, please? :confused: I am running Ubuntu 8.10...  When I open Places>Computer it does not show floppy at all.

From a terminal ```
sudo modprobe floppy
```
will load the floppy driver into the kernel.To make sure it loads on every re-boot ```
gksudo gedit /etc/modules
``` and add the word **floppy** on a newline.


That should get you going.The floppy driver was left out from 8.10 installation.

Good Luck

---

### Post by glenngds2007 on 2009-01-07
big time thank-you:D

---

### Post by Titan8990 on 2009-01-07
To avoid opening that file and potentially causing problems you can do something like the following:

```

sudo echo 'floppy' >> /etc/modules
```

---

