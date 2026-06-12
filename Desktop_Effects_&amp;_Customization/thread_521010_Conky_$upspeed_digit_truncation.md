---
title: "Conky $upspeed digit truncation?"
date: 2007-08-08
forum: Desktop Effects &amp; Customization
---

### Post by dbw6993 on 2007-08-08
Does anyone know how the Conky $upspeed variable is populated? It seems to truncate to a maximum of 4 digits... No such error from the $downspeed variable... There appears to be a leading or trailing digit missing, visible even without network traffic...

I've installed version 1.4.5-0ubuntu1 from the official repos...

Nothing fancy in the conkyrc file:
```
TEXT
${downspeed eth0}Kb/s (${totaldown eth0})
${upspeed eth0}Kb/s (${totalup eth0})
```

---

