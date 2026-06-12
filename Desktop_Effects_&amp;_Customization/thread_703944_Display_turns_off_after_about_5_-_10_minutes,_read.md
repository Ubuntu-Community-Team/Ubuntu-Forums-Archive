---
title: "Display turns off after about 5 - 10 minutes, read other fixes, have a problem"
date: 2008-02-21
forum: Desktop Effects &amp; Customization
---

### Post by mattstakilla on 2008-02-21
so i have read the fixes where is says to add

Option "BlankTime" "0"
Option "StandbyTime" "0"
Option "SuspendTime" "0"
Option "OffTime" "0"

to the end of the file but when i do that it says i dont have the permissions to save the file. now im the only user on the computer and i thought i made myself an administrator er whatever. how can i get this fixed?

---

### Post by yabbadabbadont on 2008-02-21
Use gksudo to run gedit from a terminal window when editing the file.

For further details, see: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

