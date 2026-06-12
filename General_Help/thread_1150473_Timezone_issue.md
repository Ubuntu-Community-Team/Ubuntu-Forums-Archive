---
title: "Timezone issue"
date: 2009-05-06
forum: General Help
---

### Post by boert89 on 2009-05-06
Hello,

after updating to Ubuntu 9.04 I've got a problem with my system clock. Hwclock is set to CEST, as I have to have Windows on my computer for work. Timezone is set to Europe/Vienna and in /etc/default/rcS UTC is set to "no".
Still, when I'm booting my laptop, gnome will be two hours ahead (which is the time difference between CEST and UTC), but hwclock still shows the right time. It seems that even though UTC="no", during bootup hwclock is interpreted as UTC and 2 hours are added.

Anyone else experiencing this problem or is there just a simple solution I haven't found yet (I've been looking into it since my distupgrade last week).

Thanks a lot,

Bert

---

### Post by sahabcse on 2009-05-06
Pls follow below url for fixing the time and date issue

[http://sahabm.blogspot.com/2009/02/date-and-hardware-colck-change-ubuntu.html](http://sahabm.blogspot.com/2009/02/date-and-hardware-colck-change-ubuntu.html)

---

### Post by boert89 on 2009-05-06
Sorry, there's one thing I've forgot to mention:

Manually changing the clock (or syncing to a time-server) doesn't help anything. After reboot, hwclock will show the right time, but gnome will (again) be two hours ahead.

Thank's for your answer, sahabcse, but I've tried all of this already...

---

### Post by boert89 on 2009-05-08
I'm still working on this. Anyone got an idea?

---

### Post by jflaker on 2009-05-08
> **boert89 said:**
> I'm still working on this. Anyone got an idea?

Have you tried setting your hardware clock to Zulu/GMT then using the timezone in your OS's to display the right time???

---

### Post by boert89 on 2009-05-09
I've got Windows on the computer as well, so unfortunately that's not an option...

---

