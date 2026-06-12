---
title: "cpu usage 100%"
date: 2006-02-04
forum: Desktop Environments
---

### Post by kasemodz on 2006-02-04
Alright from the past 24 hrs, my ubuntu server cpu usage is at 100%. I went to system monitor and looked at the processes and resources but it didn't help. In the processing, only 178mb of 768mb was used. In the processing the highest cpu usage program was vino-server which was taking 6 percent of cpu. How do I know which process is taking up a lot of cpu?

---

### Post by taurus on 2006-02-04
May want to check out "top" to see which one is chewing up your CPU...

---

### Post by kasemodz on 2006-02-04
hey taurus, what do you mean check out "top"?

---

### Post by az on 2006-02-04
Open a terminal and run
top


You can also try 

sudo top

So that you can kill (press "k" and then the pid number) the process if it is not owned by you.

---

### Post by kasemodz on 2006-02-04
ok i just checked and according to top, the overall cpu usage is like 9 percent however in system monitor says 100 percent. Bug maybe? Here is a screenshot.

Btw its 38 percent overall b/c i took a screenshot.

---

