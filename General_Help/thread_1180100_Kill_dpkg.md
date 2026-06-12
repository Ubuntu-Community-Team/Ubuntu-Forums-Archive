---
title: "Kill dpkg?"
date: 2009-06-06
forum: General Help
---

### Post by geofff on 2009-06-06
I was following instructions to install clamdrib to scan Thunderbird mail and in terminal entered  "sudo dpkg-reconfigure clamav-base". I then made a mistake in setting the defaults and didn't know how to get out of it, so I just closed the terminal window. Big mistake! 

Now when I re-enter "sudo dpkg-reconfigure clamav-base" I get: 
"debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable"

Having searched other posts I'm not sure whether I should kill the process by "kill dpkg" or some variant on this or to use dpkg -r, or is there something else I should do?

I'd appreciate help before I mess up further

Thanks

Geoff

---

### Post by sisco311 on 2009-06-06
```
sudo pkill dpkg
```
```
sudo dpkg-reconfigure -f gnome clamav-base
```

The default frontend can be permanently changed by:
```
sudo dpkg-reconfigure -f gnome debconf
```

In the "dialog" interface you can use the arrow keys, TAB, Space and Enter.

---

### Post by geofff on 2009-06-06
sisco311 thanks for the very quick reply. It helped me to get the emailscanner working. It was a bit disconcerting to find I'd got a trojan in my inbox even when all the messages had been cleared out of it. This has been sorted and I now feel more at ease with the scanner working. Thanks again.

---

