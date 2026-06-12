---
title: "Tracker-index ?"
date: 2009-06-06
forum: General Help
---

### Post by WILL_CHAN on 2009-06-06
I'm currently running Ubuntu 9.04. I've just received a message about tracker-index... They said
> 
Tracker 
There was an error while performing indexing :
Index corrupted 
                    ->[ Reindex all content ]

Then I restarted my pc and it is extremely slow now. It lagged every 3s I believe :(. Anyone could help me out with this ?

---

### Post by Soul-Sing on 2009-06-06
```
sudo apt-get install tracker-utils
tracker-processes -r
```

---

### Post by WILL_CHAN on 2009-06-07
Thanks a lot leoquant, it works ;) ! Love you T_T !

---

