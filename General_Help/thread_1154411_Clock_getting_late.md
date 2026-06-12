---
title: "Clock getting late"
date: 2009-05-09
forum: General Help
---

### Post by sussa on 2009-05-09
Hey everybody,

I'm using Ubuntu 9.04, and the system works like a charm. But my clock is always late, sometimes, more than 30 minutes! I'd like it to synchronize with some internet server, but I don't know how to do it. Could you please give me some help? Thanks!


p.s.: Maybe this is happening due to an error, because it seems that Ubuntu can't synchronize with the BIOS clock. Is that possible?

---

### Post by Tipped OuT on 2009-05-09
Try to set your time zone again. That fixed it for me.

---

### Post by dLeon on 2009-05-09
GUI way:
Menu > System > Time & Date
It self explanatory. You can set your time server here. While you can choose to sync manually you will need NTP package to do automatic synchronization.

CLI way:
Open terminal, type: sudo ntpdate -u ntp.ubuntu.com
ntpdate package is intalled by default with Ubuntu.
To set Timezone in terminal: sudo timezone 'yourtimezone'
Check /etc/timezone for timezones set.

About possibility that BIOS date doesn't get updated... I'm not sure about it. The only time-date error I get is always after Ubuntu setup. What ever I try; for some reasons the setup always give me 1 day ahead for my timezone. Luckily I use Ubuntu with my desktop, mean I don't know what will happen if my system is a server.

---

