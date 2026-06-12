---
title: "Accessing Vista safe mode in grub?"
date: 2010-02-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by severemacaw on 2010-02-12
I have a friend with a dell pc with vista/ubuntu dual boot. He needs to access vista safe mode, no option in grub for vista safe mode. How can he access it? Also in partitioning his drive for ubuntu he alloted 20gb and when ubuntu loads there is not enough disk space to  even install ubuntu updates. How do we reformat his drive to handle ubuntu correctly? Thanks in advance for your help.

---

### Post by CJay554 on 2010-02-12
Safe mode is accessed directly from the microsoft bootloader, but you are using Grub as your boot loader. What happens is when you choose to load Microsoft Vista, the Grub gives control to the Windows boot loader, from that point you can press the f8  key to access safe mode.

(you have to press the f8 RIGHT after you press enter on the grub menu, because it moves reaaaally fast.)

---

