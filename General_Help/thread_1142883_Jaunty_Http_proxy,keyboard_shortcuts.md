---
title: "Jaunty Http_proxy,keyboard shortcuts"
date: 2009-04-29
forum: General Help
---

### Post by rohit2412 on 2009-04-29
1) This is some problem i cant understand......

i had earlier configured http_proxy in System=>preferences=>network proxy(some reason)
Then disabled it

but now even after rebooting i see $http_proxy as setuped for proxy(without any username and password though(why??))

the variable is not instanted in .bashrc nor /etc/bash.bashrc

any ideas???

2) the usual shortcuts alt + f1,alt+f2 dont work ...nor my defined one in keyboard shortcuts gui.....

Also ,can this have anything to do with that i installed ubuntu tweak(from their own ppa repo)......

---

### Post by rohit2412 on 2009-04-30
anyone???

---

### Post by rohit2412 on 2009-04-30
Problem solved.....
(Stupid solutions...wonder why they even work!!)
1) had set $http_proxy to "" in bash.bashrc for a single boot...removed it after...
and problem solved...wonder why!!!

2) removed all .gnome .gnome2 folders........default settings galore it works!!!

---

