---
title: "A driver for your hardware is not available (NIC)"
date: 2009-02-15
forum: Debian
---

### Post by glotz on 2009-02-15
Hello there!

Just burned me a Lenny disk but the installer says there's no driver for my network card. I actually tried 3 different NICs, same results. (All the NICs work in Ubuntu.)

I wonder what now?

---

### Post by Hallvor on 2009-02-16
If you really want to use Debian: Buy one of these and use it in client-bridge mode? Then you can sell the wireless NIC and use the ethernet port. :)

[http://www.linuxdevices.com/news/NS4729641740.html](http://www.linuxdevices.com/news/NS4729641740.html)

---

### Post by glotz on 2009-02-16
All my NICs are wired since it's a desktop box. Is there a list of compatible devices somewhere? Or uncompatible?

---

### Post by Bachstelze on 2009-02-16
How can you expect us to help you if you don't give information about your NICs?

```
lspci -nn | grep -i ethernet
```

---

### Post by glotz on 2009-02-16
I expect you to help me politely and in an expert manner. :mrgreen:

Here's the output
00:0d.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)

The other cards are another Realtek and a 3Com.

---

