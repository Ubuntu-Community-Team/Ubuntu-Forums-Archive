---
title: "KDE 4.3 kdepim Google Calendar"
date: 2009-06-10
forum: Desktop Environments
---

### Post by Naatan on 2009-06-10
Hi, in the KDE 4.3 release schedule ([http://techbase.kde.org/Schedules/KDE4/4.3_Feature_Plan](http://techbase.kde.org/Schedules/KDE4/4.3_Feature_Plan)) I see that "Google calendar and contacts resource" should be added to kdepim. The task is set as completed.

I've looked through kontact and korganizer but found no reference to google calendar or google contacts. Does anyone know if this feature is available in the latest KDE 4.3 beta? And if so, how can I access it ?

Thanks

---

### Post by Lindsay.Mathieson on 2009-06-11
Yah, I've been searching high and low for it as well (no luck). This would be a biggish deal for me.

---

### Post by GeneralZod on 2009-06-11
I'm guessing it's this:

[http://websvn.kde.org/trunk/extragear/pim/googledata/](http://websvn.kde.org/trunk/extragear/pim/googledata/)

---

### Post by Lindsay.Mathieson on 2009-06-11
I had a go at building, had to build the google libs from source as well, then ran into problems with cmake not finding the kcfg_generate_dbus_interface macro.

Karmic Koala looks like it has the neccessary libs - I suspect it will only be in that. I'm going to try the Alpha2 in a Virtual PC.

---

### Post by Naatan on 2009-06-12
I installed Karmic yesterday but can't find it on there either.. I  guess you have to build it.

---

### Post by Lindsay.Mathieson on 2009-06-12
Bummer, but thanks. Couldn't get it installed on VirtualBox.

---

