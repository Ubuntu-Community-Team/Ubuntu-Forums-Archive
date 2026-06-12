---
title: "gnome power management"
date: 2010-03-26
forum: Desktop Environments
---

### Post by xpd259 on 2010-03-26
I want to change the power management settings from 2 hours to 5 hours but i'm stuck with 2 or nothing 

I've had a look in the gconf-editor but nothing jumps out 
and the AC_ settings are all at 0

any help would be fantastic


D

---

### Post by Kulgan on 2010-03-26
In gconf-editor:
Apps &#8594; gnome-power-manager &#8594; timeout
Set sleep_computer times to the number of seconds, ie for sleeping after 5 hours when on AC, sleep_computer_ac=18000.
0 just means it will never hibernate.

---

