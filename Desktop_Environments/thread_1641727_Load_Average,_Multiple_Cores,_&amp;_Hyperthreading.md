---
title: "Load Average, Multiple Cores, &amp; Hyperthreading"
date: 2010-12-09
forum: Desktop Environments
---

### Post by Xanko on 2010-12-09
I recently upgraded to a core i3 system (2 cores and 2 hyperthreads showing up as 4 "CPU"s in top, htop, etc.) My load averages when really taxing the system goes to about 1.5ish. The system does not stutter one bit however I was wondering if I should consider having a load average of 2.0 or 4.0 as really taxing the system?

Good Article on Load Averages: [http://blog.scoutapp.com/articles/2009/07/31/understanding-load-averages](http://blog.scoutapp.com/articles/2009/07/31/understanding-load-averages)

---

### Post by jbencic on 2010-12-21
from the link you posted it looks like a load average of 4 (1 x number of cpu's) is where you will experience issues (waiting/queuing)

(i believe) the load average is a cumulative average of all the cores however what if one of the cores was maxed out with a load average of the > 1 and the others were idle?

how can you list the load average per core

---

