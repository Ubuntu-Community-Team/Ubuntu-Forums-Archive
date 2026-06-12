---
title: "synaptic package manager not working, and other problems"
date: 2008-12-03
forum: General Help
---

### Post by settheworldablaze on 2008-12-03
Hi, i need a lot of help:p First, synaptic package manager dose not work, this is the error that comes up when i try to open it.

E:dpkg was interrupted, you must run 'dpkg --configure-a' to correct problem
E: _cache->open()failed, please report.

I tried to run 'dpkg --configure-a' in terminal, and i am afraid to do anything in there for i might make things worst :p 

second problem i am having is I cant put up a background anymore, or change the look of anything.

Third is when the loader for picking OS comes up, there are three ubuntus, and they all go to the same one.

Fourth thing is when i load a ubuntu, it starts to do a hard drive cheek, if i dont skip it, it fails and ubuntu dose not start.


Thank you to anyone who can help me.

---

### Post by mhh91 on 2008-12-03
for the first problem,just run the command,it's harmless,and it fixes any errors that might have happened with synaptic

for the third problem,the three ubuntus you see are kernel versions,they don't change anything in the operating system itself,but they're useful in case one of them fails

unfortunately,i can't help you with the second and the fourth ones

---

### Post by todak on 2008-12-04
The command you need to use is ```
sudo dpkg --configure -a
```

---

