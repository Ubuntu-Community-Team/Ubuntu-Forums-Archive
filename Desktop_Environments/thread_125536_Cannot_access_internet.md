---
title: "Cannot access internet"
date: 2006-02-04
forum: Desktop Environments
---

### Post by ubundumb on 2006-02-04
I'm extreme linux newbie. I installed Ubuntu (5.10) yesterday by selecting advanced options in install, because I like options (I left everything I did not know to default settings).

When I type a name and password at login, it complains that could not set up access to internet and options are to try again or login anyway. If I login anyway, firefox isn't able to connect anywhere, even when I type ip number instead of domain name. When I try "sudo" commands in the terminal, I get "sudo: unable to lookup ubuntu via gethostbyname()". My hardware is nf2 chipset. Dual booting to w*ndozes works and the net access there works without a problem.

Thanks in advance for any help.

---

### Post by ESPOiG on 2006-02-04
well is it dialup or adsl or cable or wateva

nd then does it need an ip do u need settings or wat

---

### Post by ubundumb on 2006-02-04
The machine is connected to a router (which is itself to a cable). Interesting enough I tried knoppix live cd on an other machine (behind this same router) and I did not need to configure anything, it worked straight away.

---

### Post by ESPOiG on 2006-02-04
strange

---

### Post by Jakg on 2006-02-04
hmmm, running a DWL-510 Wireless D-Link card and i cant connect either, i dont know that much about Linux, what should i do? its not vitally important as im going back on lan in a week, but still

---

### Post by Ramses de Norre on 2006-02-04
Have you've got everything configured correctly? (system > administration > networking). It isn't wireless? What does $ ifconfig say?

---

### Post by ubundumb on 2006-02-04
If I recall correctly the pane, it said something that no network device, or something like that. There was a "configure" button and when pressed it opens a window which is blank, when I try to close it, I will be asked if I would like to force a shotdown of that task. Should I reinstall? :( How can I reinstall it so that I will not mess my partitions and the boot loader, so that it would simply install itself to the same partition(s) that it currently resides?

---

### Post by Ramses de Norre on 2006-02-06
Just run the install and choose the right partition when asked..
But there may be a better way to fix this, though I wouldn't know how..

---

