---
title: "ttink"
date: 2006-01-05
forum: General Help
---

### Post by YanH on 2006-01-05
Has anybody managed to get ttink to work sucessfully? I am trying to use it with an Epson Photo Stylus 950 on a Server running Breezy but the message I always get even if running as root is 

root@host:/etc/init.d# ttink -d /dev/lp0
No access to device file or no attached printer.

Any help would be much appreciated as trying to guess which of the six ink cartirdges has run out is driving me crackers:(

---

### Post by 5-HT on 2006-01-05
Hey, I haven't heard of ttink, nor could I find it in the available packages so I can't be of much help there...did you mean mtink by any chance?

What I like to use is escputil, which is a great, and extensive but lightweight CLI Epson Stylus printer utility without many dependencies.

It's very simple to use, but if you want to check it out and run into some problems I'm sure myself of others can most likely help you out.

---

### Post by YanH on 2006-01-05
ttink is the command line version of mtink. I can't use mtink as the printer is attached to a server without X installed.

---

