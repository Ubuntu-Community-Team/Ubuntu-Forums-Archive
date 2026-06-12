---
title: "Samsung DVD player + Dell?"
date: 2009-05-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Thanatios on 2009-05-07
Greetings!

It seems that my dell Dimension isn't able to see my Samsung CDRW/DVD Player. Is there an workaround or something for this issue?

Thanks in advance!

---

### Post by coffeeaddict22 on 2009-05-07
Hi,
What's the output of ```
cat /etc/fstab
```
This should show the filesystems your PC is aware of; if the CD is in there then it should be simply a matter of mounting it.

---

