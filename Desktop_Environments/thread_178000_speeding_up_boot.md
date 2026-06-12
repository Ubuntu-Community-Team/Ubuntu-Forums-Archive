---
title: "speeding up boot"
date: 2006-05-17
forum: Desktop Environments
---

### Post by rkakkar on 2006-05-17
while loading ubuntu.. one of the items states 'synchronizing clock with ...' some ubuntu internet address. since i'm on dial up this will always fail. as a result how do i disable this at boot up?

---

### Post by fuzzymallets on 2006-05-17
I think by going to System -> Administration  -> Services and unchecking the Clock synchronizatoin service (ntpdate) will disable it.

---

### Post by fuzzymallets on 2006-05-17
If that doesn't work you can try 

sudo update-rc.d -f ntpdate remove 

this will remove the ntpdate from starting at boot.

---

### Post by rkakkar on 2006-05-18
thanks! :)

---

### Post by Ramses de Norre on 2006-05-18
If you're dual booting this can cause a wrong time in windows, because ntpdate is also responsible for updating the hardware clock (used by windows to synchronize).

---

