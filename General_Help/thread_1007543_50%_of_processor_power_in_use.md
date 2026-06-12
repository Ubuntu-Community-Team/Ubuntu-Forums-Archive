---
title: "50% of processor power in use?"
date: 2008-12-10
forum: General Help
---

### Post by Wickd on 2008-12-10
After about thirty minutes into Ubuntu (8.10), my processing power usage increases to a constant 50%. If I look in the processes tab of the Resource Manager it does not show any guilty processes? Where can I have a look to find the offender?

Thanks

---

### Post by taurus on 2008-12-10
Maybe updatedb is running.  Open a terminal and run top.

```
top
```

---

### Post by Wickd on 2008-12-10
Never heard of it :) If it is that, where do I turn it of? I did a restart about ten minutes ago and seems to be fine. I also noticed after running wireshark (before I shut down), that there is 1 connection that appears to be requesting informarmation

---

