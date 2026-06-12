---
title: "Phantom data is causing HDD to be reported as full - no it isn't."
date: 2009-06-13
forum: General Help
---

### Post by CK05 on 2009-06-13
Hi, 

Both Nautilus and Disk Usage Analyser are reporting that my main Ubuntu HDD is full (94% or 100gb of 110gb). 


The thing is....when I change the Disk Usage Analyser mode to scan where all this data is from, the numbers do not add up! I can't find out where this data is even right clicking on Nautilus folders and adding up all the numbers it doesn't add up. 

Does anyone know where I can find phantom data?

---

### Post by dcstar on 2009-06-13
> **CK05 said:**
> Hi, 

Both Nautilus and Disk Usage Analyser are reporting that my main Ubuntu HDD is full (94% or 100gb of 110gb). 


The thing is....when I change the Disk Usage Analyser mode to scan where all this data is from, the numbers do not add up! I can't find out where this data is even right clicking on Nautilus folders and adding up all the numbers it doesn't add up. 

Does anyone know where I can find phantom data?

```
gksudo baobab
```

---

### Post by CK05 on 2009-06-13
Awesome, that's done the trick, the data now shows up under 

root/local/share/trash/files 

Thank you.

---

