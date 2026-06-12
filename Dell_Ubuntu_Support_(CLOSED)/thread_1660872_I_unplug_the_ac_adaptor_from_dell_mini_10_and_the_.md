---
title: "I unplug the ac adaptor from dell mini 10 and the computer shuts down"
date: 2011-01-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by irh1991 on 2011-01-05
I am running Ubuntu on a dell mini 10 netbook and I have a problem with the power management. Basically as soon as I unplug the ac adapter when I am charging, the computer gives me a message saying the power is critically low (a minute left) and must shutdown. 

This happens no matter the level of the battery, it can be 20% or 100% the computer still turns off. Its strange because the netbook recognizes it is fully charged before and after I unplug the charger. I can run the acpi command before unplugging and get 50%. After I disconnect there is some time between the messsage appearing and the computer shutting down. I can run the acpi command after receiving the message and I can still get 50%. Regardless of this the computer still shuts down. 

And its not a battery issue becuase it doesnt happen when I run windows. 

help would be a godsend!

---

### Post by mikewhatever on 2011-01-06
I had the same problem in the Dell mini 10, but there was an easy fix. Launch gconf-editor from a terminal and navigate to **/apps/gnome-power-manager/general**, uncheck the use_time_for_policy box.

---

