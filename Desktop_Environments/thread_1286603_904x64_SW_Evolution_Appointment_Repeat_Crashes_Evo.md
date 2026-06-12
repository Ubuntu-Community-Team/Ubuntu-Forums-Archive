---
title: "904x64: SW: Evolution:: Appointment Repeat Crashes Evolution"
date: 2009-10-09
forum: Desktop Environments
---

### Post by xerman on 2009-10-09
Hello there:

I am running a Desktop machine with Ubuntu 904x64. And i came to an issue with Evolution Calendar:

Whenever i try to Make an appointmet repeat Evolution Crashes and quits. I've ran evolution from Terminal with the following results:

```
a@b:~$ evolution
** (evolution:6011): DEBUG: mailto URL command: evolution %s
** (evolution:6011): DEBUG: mailto URL program: evolution
** (evolution:6011): DEBUG: EI: SHELL STARTUP

(evolution:6011): calendar-gui-CRITICAL **: simple_recur_to_comp: assertion `GTK_BIN (priv->special)->child != NULL' failed
Fallo de segmentación

```

"Fallo de segmentación" == "Segmentation Fault".

So i can not make any looped entries in the calendar. Which is very annoying.


Would appreciate any light can throw on this issue. 

Best Regards.

Xermán

---

