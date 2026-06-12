---
title: "Monitor standby with XGL"
date: 2006-08-30
forum: Desktop Environments
---

### Post by Aglarond on 2006-08-30
I have XGL/Compiz (KDE) working great except for one thing: my monitor won't go into standby on it's own. If I do a 'dpms 0 5 0' or anything along those lines, it'll go into standby, so I know my xorg config is right in that respect. 

Option          "DPMS"
Option          "StandbyTime"   "1200"

Is there anything else I should add? This config works in X 7.0.

Thanks
Mike

---

### Post by Moloko on 2006-10-22
> **Aglarond said:**
> 
Option          "StandbyTime"   "1200"


Have in mind that in the xorg.conf file the format for the time is in minutes, 1200 minutes is a long time :D , but if you use xset from the terminal is in seconds ... this works for me, 3 minutes in this case:

```

Section "ServerFlags"
   Option "StandbyTime" "3"
EndSection
```

---

### Post by Aglarond on 2006-10-22
That's what I didn't understand. Thanks for the clarification; it was a huge help. I'd assumed xset was the same. :)

---

