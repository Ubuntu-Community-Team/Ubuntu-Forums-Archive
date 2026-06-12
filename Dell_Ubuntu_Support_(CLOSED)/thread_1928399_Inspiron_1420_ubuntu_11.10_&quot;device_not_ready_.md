---
title: "Inspiron 1420 ubuntu 11.10 &quot;device not ready firmware missing&quot;"
date: 2012-02-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by michael15 on 2012-02-20
Alright, so I am installing ubuntu 11.10 on my dell inspiron 1420, and it says on the wireless button "device not ready firmware missing"
How can I fix this?
I need internet on ubuntu!

---

### Post by wildmanne39 on 2012-02-21
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

