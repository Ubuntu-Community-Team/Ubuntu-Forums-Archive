---
title: "Wirless help , Dell XPS M1330"
date: 2011-07-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by abdkamel on 2011-07-31
Dear all,
thanks for your time, my problem is I installed the new **Ubuntu 11.04** to see that my wireless  connection is not working, i checked the **driver, and it seems to be installed**, the only problem is i cannot connect to the internet, **cannot discover any wireless connection**, 
my card is **Dell wireless 1490 dual band mini card**.
any help to diagnose this problem will be appreciated.

---

### Post by mikewhatever on 2011-08-02
Hi, and welcome to the forums.
You'll need to provide some more info about the problem.
Please post the outputs of the following commands:

```
lspci

sudo lshw -C network

lsmod | grep -e b43 -e wl
```

---

