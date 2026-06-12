---
title: "smb4k cannot connect"
date: 2006-08-22
forum: Desktop Environments
---

### Post by petervdv on 2006-08-22
Hi,
I installed smb4k smbfs .
When I try to connect with the client I am getting this error:
smbmnt must be installed suid root for direct user mounts (1000,1000)
smbmnt failed: 1.

How can I solve this please?

---

### Post by nilfilter on 2006-08-22
[http://smb4k.berlios.de/handbook/faq_mounting_unmounting.html#id336614](http://smb4k.berlios.de/handbook/faq_mounting_unmounting.html#id336614)

---

### Post by petervdv on 2006-08-23
Thank you so much nilfilter
problem solved

---

### Post by rickc on 2006-09-16
Fixed my prob too... Good thing for the search button up there. Thanks again nilfilter

---

### Post by duhblow7 on 2006-09-16
here's the fix:

```
sudo chmod +s `which smbmnt`
```

also use this to unmount shares:

```
sudo chmod +s `which smbumount`
```

---

### Post by Antman on 2006-09-24
Worked like a charm - thanks.;)

---

