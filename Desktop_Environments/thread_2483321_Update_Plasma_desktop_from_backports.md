---
title: "Update Plasma desktop from backports"
date: 2023-01-26
forum: Desktop Environments
---

### Post by enricobe on 2023-01-26
Hello,
I'm running the last version of Kubuntu but I'd like to have the last KDE Plasma updates. I find that the backports PPA should let me update the Plasma packages but I can't fully understand if this is the right way (if any) to get cutting edge Plasma packages.

Can I install the kubuntu backports PPA on Kubuntu 22.10 and get the last plasma updates?

---

### Post by monkeybrain20122 on 2023-01-27
Install ppa-purge first (it is in repo). if something goes wrong you can just purge the ppa (removing the ppa is not good enough since you want to downgrade all the packages)

To use it 

```
sudo ppa-purge ppa:kubuntu-ppa/backports
```

---

### Post by enricobe on 2023-01-28
thank you very much for your help, it all worked fine!

---

