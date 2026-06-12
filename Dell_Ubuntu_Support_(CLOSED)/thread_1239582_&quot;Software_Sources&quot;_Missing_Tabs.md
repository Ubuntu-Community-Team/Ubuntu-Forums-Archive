---
title: "&quot;Software Sources&quot; Missing Tabs"
date: 2009-08-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by VitoDe on 2009-08-13
I'm a Linux newbie using Ubuntu 8.04 Hardy (Long Term Edition) on a Dell Mini 9 netbook.  I've received no updates in over two months, and noticed that under Administration / Software Sources, I'm now missing three of the tabs, including "Ubuntu Software," "Updates" and "Statistics."  I'm guessing that their absence is causing my lack of updates.  Any way a mere mortal could get these tabs back and once again start receiving updates?  Would it be easier -- if it's possible -- to rid the netbook of Dell altogether and, if it's possible, simply to install Ubuntu 9.04?  I've sent for the 9.04 CD.  Thanks!

---

### Post by aysiu on 2009-08-14
I don't know why those tabs disappeared or how to get them back, but you can manually get updates by simply going to System > Administration > Synaptic Package Manager, clicking Reload, Mark All Upgrades, and then Apply.

If Synaptic isn't in your menus, you can also paste this command into the terminal: ```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by VitoDe on 2009-08-15
Thanks, Aysiu.  I'll try it.  If it doesn't work, would installing version 9.04 run on my Dell Mini 9 and rid the netbook of any Dell influence in the software?

---

