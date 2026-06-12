---
title: "Changing Fluxbox clock format"
date: 2006-11-11
forum: Desktop Environments
---

### Post by paul6 on 2006-11-11
I am trying to change the Fluxbox clock format so that it includes todays date.  (i.e. "11-23-06 4:53") I know I can right click on the Fluxbox clock and choose "Edit Clock Format" and a popup will come up with this info:
"%l:%M" My question is what do I change it to, so that it include's todays date?

Thanks
Paul

---

### Post by scooper on 2006-11-12
If you run "date --help" or "man date" from a command line it should give you the valid formats for what fluxbox accepts.  They all probably use the C strftime function.  You can probably also run "man strftime" to get the same format strings.  Using the command line date command will allow you to conveniently play with it until you get it right.

Something like "%m-%d-%y %H:%M" should get you close. :)

---

