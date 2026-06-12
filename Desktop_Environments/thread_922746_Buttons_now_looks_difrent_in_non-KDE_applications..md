---
title: "Buttons now looks difrent in non-KDE applications."
date: 2008-09-17
forum: Desktop Environments
---

### Post by chrisruls00 on 2008-09-17
After I updated something along the likes of Qtk, All the buttons and scrollbars etc. changed to some old windows 98 looking boring style. I checked my system settings but nothing changed! I even made sure that "use KDE theme for non-KDE applications" Option was checked. I assume the upgrade changed something. Can anyone help?

---

### Post by Daisuke_Aramaki on 2008-09-17
> **chrisruls00 said:**
> After I updated something along the likes of Qtk, All the buttons and scrollbars etc. changed to some old windows 98 looking boring style. I checked my system settings but nothing changed! I even made sure that "use KDE theme for non-KDE applications" Option was checked. I assume the upgrade changed something. Can anyone help?

assuming ur talkin about kde 3.5 and u installed the gtk-qt-engine update that was made available yesterday? if yes, then this wud help. the update that u installed is directed at kde4.1 users, but it installs over the current engine, thereby screwing up and totally removing the configuration option as well from the kde control center. here is how i reset the  thing.

goto synaptic. search for gtk-qt-engine. it will show u the latest installed version. mark that and go to Package->Force Version and u shud get another package, the one that u had before. choose that and install the package again. the settings wud return! hope that helps!

---

### Post by james_xxx on 2008-09-18
How does one do this without synaptic (which most Kubuntu users do not use)?

---

