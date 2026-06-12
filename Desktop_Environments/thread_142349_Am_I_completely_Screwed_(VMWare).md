---
title: "Am I completely Screwed (VMWare)"
date: 2006-03-10
forum: Desktop Environments
---

### Post by %hMa@?b&lt;C on 2006-03-10
I created a virtual machine, and then deleted it because i was just testing, and now i have lost 8 Gigs of Hard disk space, which I cant seem to get back. Any help would be appreciated. and i also emptied my trash since then.

---

### Post by taurus on 2006-03-10
Make sure you remove everything in ~/.vmware (or even ~/vmware if you have it) too...

---

### Post by %hMa@?b&lt;C on 2006-03-10
still says the same HDD Space

---

### Post by taurus on 2006-03-10
Where did you install vmware and were you the only one who ran it?

---

### Post by lamego on 2006-03-10
The only way you could lose such space is with a vm disk file.
Just:
```
  find / -name "*.vmdk"
```
 to look for it.

---

