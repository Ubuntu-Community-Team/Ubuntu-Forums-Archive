---
title: "Planeshift installing error - Dialog program?"
date: 2006-02-01
forum: Gaming &amp; Leisure
---

### Post by ipp3l1 on 2006-02-01
When I try to install PlaneShift in terminal ( sh package.run ), i get this error :
```

Creating directory ps.cb.03.011.linux.x86-2
Verifying archive integrity... All good.
Uncompressing Planeshift Crystal Blue Version 3.011 relase 2..
Checking if dialog program is installed...
Dialog program, which is required to use this software, cannot be found.
Please install this program before continuing Planeshift installation.
You may obtain it from your distribution FTP or install disk.

```

What is that Dialog program and how can I install it?

---

### Post by Perfect Storm on 2006-02-01
You have to enable universe in your sourcelist. Then:

```
sudo apt-get install dialog
```

---

### Post by ipp3l1 on 2006-02-01
Thank you \\:D/

---

