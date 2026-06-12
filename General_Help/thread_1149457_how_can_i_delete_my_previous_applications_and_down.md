---
title: "how can i delete my previous applications and downloads??"
date: 2009-05-05
forum: General Help
---

### Post by sanozuke02 on 2009-05-05
anyone ?? help me.. i want to delete my previous downloads and installed applications... 


 please help me.. because my memory it too low now..

---

### Post by Grenage on 2009-05-05
Are you talking about installed application via apt?  You should be able to remove them via the Synaptic Package Manager.

---

### Post by plucky on 2009-05-05
From a terminal

```
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
```

See **man apt-get** for what these commands do.

> please help me.. because my memory it too low now.. 

Do you mean drive space is low? Because drive space and memory are two different things.

Good Luck

---

