---
title: "System Monitor &amp; Conky report different memory usage?"
date: 2009-01-25
forum: General Help
---

### Post by switchseven on 2009-01-25
Can anyone explain why my System Monitor and Conky are reporting different memory usage? 34.3% and 98%.

Is conky reporting assigned memory, and gnome-system-monitor reporting used memory? Is there a difference?

For those who know conky, i'm using $membar and $mem.

Screen attached.


Cheers all,

Dave.

---

### Post by The Cog on 2009-01-25
Try setting no_buffers to no in .conkyrc. no_buffers tells it to not show the memory used for system buffers.

---

### Post by switchseven on 2009-01-25
Set no_buffers to yes.
Worked great - thanks!

---

