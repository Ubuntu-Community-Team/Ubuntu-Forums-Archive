---
title: "desktop effects could not be enabled..."
date: 2009-04-24
forum: General Help
---

### Post by 84loops on 2009-04-24
that's what I get when I try to enable my desktop effects. They worked ok when I was using 8.10. I updated the system today and now I don't have effects. How do I solve this problem?

---

### Post by Peter09 on 2009-04-24
What is your graphics card

```
lshw -C video
```

---

### Post by 84loops on 2009-04-24
here is my graphics info

WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 82865G Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0

---

### Post by Peter09 on 2009-04-24
Look here

[http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html)

---

### Post by Peter09 on 2009-04-24
A more upto date one

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

---

### Post by blazemore on 2009-04-24
CompizCheck here: [http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

---

