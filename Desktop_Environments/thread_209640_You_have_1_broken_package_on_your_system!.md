---
title: "You have 1 broken package on your system!"
date: 2006-07-05
forum: Desktop Environments
---

### Post by mathjazz on 2006-07-05
I've just installed my Netgear WG511 PCMCIA Wireless Adapter. It only works with ndiswrapper 1.11, however 1.18 is available in the repos.

When I open the Package Manager (Synaptic), it says:
"You have 1 broken package on your system! Use the "Broken" filter to locate it."

So I cannot install any new package, neither can I update my system.

I tried forcing version 1.11, but when I tried applying changes, it wanted to remove ndiswrapper.

What should I do?

---

### Post by tseliot on 2006-07-05
Close Synaptic and type:
```
sudo apt-get install -f
```

---

### Post by mathjazz on 2006-07-05
I don't think this is a good idea, since ndiswrapper will be upgraded to 1.18, which doesn't work for my card.

Are you sure?

---

### Post by wazoo on 2006-07-05
Wouldn't it be best to do this first?

From Synaptic, choose Edit>Fix broken packages.

---

### Post by mathjazz on 2006-07-05
It's the same as apt-get -f install: it tries to upgrade ndiswrapper.

---

