---
title: "Dual Boot Ubuntu and Windows"
date: 2013-10-15
forum: Desktop Environments
---

### Post by Colin_Mills on 2013-10-15
Hello community

My machine has x2 250GB internal HDD. On sda drive I have Ubuntu 13.04 installed and sdb I have Windows Vista Ultimate installed. Both OS are recognised by my machine when manually swapping over the internal drives to sda slot.

My question is - How can I get my machine to recognise both drives on boot so I can choose which OS to boot at startup?

Any input and resources much appreciated.

TIA

---

### Post by Colin_Mills on 2013-10-15
Nevermind - solved this by updating Grub with the following command line:

```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

---

