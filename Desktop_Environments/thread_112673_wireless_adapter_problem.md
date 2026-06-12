---
title: "wireless adapter problem"
date: 2006-01-04
forum: Desktop Environments
---

### Post by dsjas297 on 2006-01-04
Okay, here's my wireless adapter story. I bought it and found out it used the Ralink rt2561 chipset, whihc I found no suitable drivers for a linux system. So I tried using ndiswrapper witho no luck. Then Ralink issues the source code for the linux driver. I clmpole it, load the module, and Ubuntu finally realizes that it can use that card and places it in the network configuration menu.

However, there are two problems.

1. The module is not loaded at system bootup.

2. When I configure the adapter, it still does not connect to the internet.

All help in solving these problems isgreatly appreciated.

---

### Post by n00b13 on 2006-01-04
i have a similar problem. 

i have a dwl g630 wireless card.
it recognized it in the network configuration screen, but would never connect so i tried ndiswrapper. still wont connect.

using wifi radar i can find my network, but it will never connect. ever.

---

