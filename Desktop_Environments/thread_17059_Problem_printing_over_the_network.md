---
title: "Problem printing over the network"
date: 2005-02-25
forum: Desktop Environments
---

### Post by Termina on 2005-02-25
I was hoping someone could help me get my printer up and running?

I'd done 'adduser cupsys shadow' and restarted cupsys. I can print just fine from the computer it's plugged in to, but when I try to print over the network (using [http://192.168.0.3:631/ipp/port1](http://192.168.0.3:631/ipp/port1)

I've also tried enabling this in the cupsd.conf file, and using [http://192.168.0.3:631/printers/DeskJet-672C](http://192.168.0.3:631/printers/DeskJet-672C).

I've googled around, and looked through this forum, but nothing I've found has helped me so far. =/ 

<Location /printers/DeskJet-672C>
AuthType None
Allow From 192.168.0.
</Location>

---

### Post by WW on 2005-02-25
This might have some useful suggestions: [http://www.ubuntulinux.org/wiki/FrequentlyAskedQuestions#networkprinter](http://www.ubuntulinux.org/wiki/FrequentlyAskedQuestions#networkprinter)

---

