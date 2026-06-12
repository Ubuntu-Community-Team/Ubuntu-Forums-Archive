---
title: "[SOLVED] How to remove the beryl"
date: 2007-09-07
forum: Desktop Environments
---

### Post by sunil.pawar on 2007-09-07
i have install beryl using command line. i just type **bery**l in home directory and enter the key, it increase the resolution of my PC,  so that i can't  see the close,minimize button in the right corner of any application and i can't switch to another application.To remove beryl what can i do?

---

### Post by astoltz on 2007-09-07
Open a terminal and enter ```
killall beryl
``` When you start beryl that way, it may not be loading the window manager - which is why you've got no close / minimize... buttons.  Try starting beryl with the command: ```
beryl-manager
```

---

### Post by speedup on 2007-09-07
You can find it under Synaptic Package and remove it there or you can go to the Add/Remove programs.

---

### Post by sunil.pawar on 2007-09-07
> **speedup said:**
> You can find it under Synaptic Package and remove it there or you can go to the Add/Remove programs.

Thank you
it work properly

---

### Post by Inxsible on 2007-09-07
Please mark your thread solved. Someone else might benefit from it. :)

Top right corner. Thread Tools --> Mark thread as solved.

---

