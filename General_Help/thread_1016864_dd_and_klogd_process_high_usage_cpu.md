---
title: "dd and klogd process high usage cpu"
date: 2008-12-20
forum: General Help
---

### Post by psychok9 on 2008-12-20
I've high usage of this 2 process (dd and klog), and the total cpu usage of core 1 go up to 100% on Acer 5920g e Ubuntu 8.10 i386.
What is dd and klogd process?
Solved only with a complete restart...

---

### Post by imopen on 2009-01-02
I have the same notebook and I have the same issue. I solve it only killing klogd by root. Any suggestion? :confused:

---

### Post by psychok9 on 2009-01-02
> **imopen said:**
> I have the same notebook and I have the same issue. I solve it only killing klogd by root. Any suggestion? :confused:

I've fixed it with last kernel 2.6.27.11 from Ubuntu proposed repository.

---

### Post by Bingulim on 2009-01-07
> **imopen said:**
> I have the same notebook and I have the same issue. I solve it only killing klogd by root. Any suggestion? :confused:

I have a HP dv6575 and the same problem. Killing *klogd* seemed to work.

---

