---
title: "kubuntu 9.10 browsing very SLOW."
date: 2009-11-02
forum: Desktop Environments
---

### Post by nettobr on 2009-11-02
Hi There,

Congrats, Kubuntu 9.10 is very fast booting and beautiful and all my devices were installed ok (fresh install).

But browsing very SLOW, in any browser - Konqueror, Firefox or Opera.

Dont know why but stalls a little for opening new tab, bringing images...

But I have a win-xp inside this Kubuntu 9.10 (using VirtualBox) and surfing is fast or normal.

Cant understand.

Does anybody have same problem???

Core 2 Duo 1.6, 2 Mb Ram...

Thanks,

NettoBr

---

### Post by tar1 on 2009-11-03
Ubuntu 9.10 installed from wubi is giving me the same problem.  Had snappy firefox with 9.04.  And it doesn't make asny difference which browser I use. Wonder if others are having the same problem with fresh install 9.10. Thanks

---

### Post by crom.osec on 2009-11-03
Check your nameservers in /etc/resolv.conf
make sure that you have the correct ones in proper order

---

### Post by tar1 on 2009-11-03
Think I found an answer.  Look at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/417757](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/417757).  This worked for me and now Firefox is back at snappy.  Hope this helps


don't know why but the above https doesn't read correctly  ie "   /+source/linux/ "    in the line is correct

---

### Post by nettobr on 2009-11-05
Ok, they found the problem, but I will wait for the formal solution.

This topic is a kind of brain-storm...

Thanks...

Nettobr

---

