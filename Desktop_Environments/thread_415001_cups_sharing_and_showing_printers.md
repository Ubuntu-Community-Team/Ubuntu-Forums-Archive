---
title: "cups: sharing and showing printers"
date: 2007-04-20
forum: Desktop Environments
---

### Post by nightfrost on 2007-04-20
I'm using the cups administration panel through localhost:631 in order to both share printers *and* detect other shared printers. What I am trying to do is to enable both of these:

[x] Show printers shared by other systems
[x] Share published printers connected to this system

The problem is that after pressing "change settings", one of them becomes disabled. It seems I can only enable one the options. Is there no way to enable both? Why is there such a restriction?

Thanks in advance.

---

### Post by dcstar on 2007-04-22
> **nightfrost said:**
> I'm using the cups administration panel through localhost:631 in order to both share printers *and* detect other shared printers. What I am trying to do is to enable both of these:

[x] Show printers shared by other systems
[x] Share published printers connected to this system

The problem is that after pressing "change settings", one of them becomes disabled. It seems I can only enable one the options. Is there no way to enable both? Why is there such a restriction?

Thanks in advance.

I just tested this on my system using the Web interface as well as System-Administration-Printing.

I had to manually restart /etc/init.d/cupsys after the change, but they both seemed to stick for me.

---

